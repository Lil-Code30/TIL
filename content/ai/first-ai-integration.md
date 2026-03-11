---
title: First AI Integration
description: A step-by-step guide to integrating AI into your application for the first time.
---

Since the beginning of the AI era, I never took the time to integrate AI into my applications. Because for me it was not that useful for my use cases. But I wanted to give it a try and see how it works. So I decided to integrate [@mistralai/mistralai](https://docs.mistral.ai/api) in a Saas I am currently building ([Learn more here](https://acadxp.vercel.app/)).

At first, I was a bit overwhelmed by the documentation and the different options available. But I decided to start with the basics and see how it works. I created an account on Mistral AI and got my API key. Then I installed the package and started experimenting with it.

I was amazed by how easy it was to use and how powerful it is. I was able to generate text, images, and even code with just a few lines of code. I also found that the documentation is very clear and easy to understand.

## Course Creation

I decided to use Mistral AI to generate course's chaellenges, skills, and badges depending on the course the user select. The results must be a json format that I can easily use in my application. I started by creating a function that takes the course name as input and returns the generated content.

> for the moment the json-schema returned by Mistral AI is not the one I want, so for future improvements I will try to make it return the exact json-schema I want. And also explore more option like image generation for the badges and skills.

## Youtube Video Creation

I did all the process live on my [Youtube channel](https://www.youtube.com/@licode30) and I will share the video here once it's published.

![11.03 | Construire un SaaS de A à Z : Épisode 17 – Le projet AcadXP](https://www.youtube.com/watch?v=vlC9d7mA3-k)

## This are some sample code

```typescript
import { Mistral } from "@mistralai/mistralai"
import { aiBluePrintSchema } from "../validation/course-blue-print.schema"
import dotenv from "dotenv"

dotenv.config()

const apiKey = process.env.MISTRAL_AI_STUDIO_API_KEY

const client = new Mistral({ apiKey: apiKey })

// System prompt to guide the AI's response
const systemPrompt = `You are AcadXP AI, an academic game designer\n Your role is to transform any academic course into a structured, gamified experience.\n You must generate skills, challenges, and badges that are:\n academically meaningful\n discipline-agnostic\nachievable by a real student\nbalanced in difficulty and XP rewards\n You must ALWAYS respond with VALID JSON.\nDo not include explanations, markdown, or extra text.`

type CourseInfo = {
  courseId: string
  courseTitle: string
  courseDescription: string
  academicLevel: string
}

// Build the user prompt based on the course information
const buildCoursePrompt = (courseInfo: CourseInfo) => {
  const { courseId, courseTitle, courseDescription, academicLevel } = courseInfo
  return `
   Generate a gamified blueprint for the following academic course.

Course ID: ${courseId}
Course title: ${courseTitle}
Course description: ${courseDescription}
Academic level: ${academicLevel}

Rules:
- Generate between 5 and 8 skills
- Generate between 3 and 5 challenges
- Generate between 2 and 3 badges
- XP must be realistic and balanced
- Challenges must reference real academic activities
- Avoid vague or generic content
- Ensure a mix of easy, medium, and hard challenges
- Use the provided course information to create relevant and engaging content`
}

// CourseAgent Creator

// let CourseAgent = await client.beta.agents.create({
//   model: "mistral-large-2512",
//   name: "CourseGenerator Agent",
//   description:
//     "An agent that generates gamified blueprints for academic courses",
//   instructions: systemPrompt,
// });

export const aiGeneratedBluePrint = async (courseInfo: CourseInfo) => {
  const userPrompt = buildCoursePrompt(courseInfo)

  const chatResponse = await client.chat.parse({
    model: "mistral-large-latest",
    messages: [
      { role: "system", content: systemPrompt },
      { role: "user", content: userPrompt },
    ],
    responseFormat: aiBluePrintSchema,
    maxTokens: 4000,
    temperature: 0.3,
  })

  return chatResponse
}
```

### AI BluePrint Schema

```typescript
import * as z from "zod"

// Individual rule schema
export const RuleSchema = z.object({
  type: z.enum(["COUNT", "SCORE", "COMPLETION", "SUBMISSION", "GRADE"]),
  target: z.string(),
  operator: z.enum(["GTE", "GT", "EQ"]),
  value: z.number(),
  metadata: z
    .object({
      courseId: z.string(),
    })
    .optional(),
})

// Criteria schema with multiple rules and logic
export const CriteriaSchema = z.object({
  logic: z.enum(["AND", "OR"]).default("AND"),
  rules: z.array(RuleSchema).min(1, "At least one rule is required"),
})

export const aiChallengeBluePrintSchema = z.object({
  title: z.string().min(10, "Title is required"),
  description: z.string().min(10, "Description is required"),
  difficulty: z.enum(["easy", "medium", "hard"], {
    message: "Difficulty level must be one of 'easy', 'medium', or 'hard'",
  }),
  xpReward: z.number().int().positive("XP reward must be a positive integer"),
  criteria: CriteriaSchema,
})

export const aiSkillBluePrintSchema = z.object({
  title: z.string().min(3, "Title is required"),
  description: z.string().min(10, "Description is required"),
  xpValue: z.number().int().positive("XP value must be a positive integer"),
  iconPrompt: z.string().min(10, "Icon prompt is required"),
  criteria: CriteriaSchema.optional(),
})

export const aiBadgeBluePrintSchema = z.object({
  title: z.string().min(3, "Title is required"),
  description: z.string().min(10, "Description is required"),
  xpValue: z.number().int().positive("XP value must be a positive integer"),
  iconPrompt: z.string().min(10, "Icon prompt is required"),
  criteria: CriteriaSchema.optional(),
})

export const aiBluePrintSchema = z.object({
  skills: z.array(aiSkillBluePrintSchema).min(3, "At least three skill is required"),
  challenges: z.array(aiChallengeBluePrintSchema).min(3, "At least three challenge is required"),
  badges: z.array(aiBadgeBluePrintSchema).min(3, "At least three badge is required"),
})

// Type inference
export type aiBluePrintSchema = z.infer<typeof aiBluePrintSchema>
```
