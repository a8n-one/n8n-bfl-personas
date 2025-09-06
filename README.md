# n8n BFL Personas - AI-Powered Marketing Automation

An automated marketing workflow system built with n8n that generates personalized marketing personas and creates AI-generated product imagery using Black Forest Labs (BFL) image generation.

## Overview

This project automates the entire marketing campaign creation process, from initial brief collection through persona generation to final image delivery. The system creates targeted marketing personas and generates corresponding product images tailored to each persona's characteristics.

## Architecture

The system consists of three main n8n workflows:

### 1. Brief Collection Workflow (`brief.json`)
- **Trigger**: Telegram chatbot
- **Purpose**: Collects campaign briefs from users through conversational interface
- **Components**:
  - Telegram trigger for user input
  - OpenAI GPT agent for intelligent brief collection
  - PostgreSQL storage for campaign data
  - Memory buffer for conversation continuity

### 2. Persona Creative Workflow (`persona-creative.json`)
- **Trigger**: PostgreSQL database trigger (when new brief is added)
- **Purpose**: Generates detailed marketing personas and creative prompts
- **Components**:
  - PostgreSQL trigger and data retrieval
  - OpenAI GPT models for persona generation
  - Structured output parsing for consistent data format
  - Image prompt generation for Black Forest Labs
  - Loop mechanism to process multiple personas
  - Sub-workflow execution for image generation

### 3. Image Generation Workflow (`img-gen.json`)
- **Trigger**: Sub-workflow execution from persona workflow
- **Purpose**: Generates product images using Black Forest Labs FLUX model
- **Components**:
  - Black Forest Labs API integration
  - Asynchronous image generation with polling
  - Telegram delivery of generated images

## Technology Stack

- **Workflow Engine**: n8n
- **AI Models**: 
  - OpenAI GPT (persona generation, brief processing)
  - Black Forest Labs FLUX (image generation)
- **Database**: PostgreSQL
- **Communication**: Telegram Bot API
- **Image Generation**: Black Forest Labs API

## Workflow Process

1. **Initial Trigger**: User interacts with Telegram chatbot
2. **Brief Collection**: AI agent collects product information, target audience, and campaign goals
3. **Data Storage**: Campaign brief stored in PostgreSQL database
4. **Persona Generation**: Database trigger initiates persona creation workflow
5. **Persona Processing**: System generates 4 distinct marketing personas with detailed characteristics
6. **Image Generation**: For each persona, creates tailored product imagery prompts
7. **Image Creation**: Black Forest Labs generates high-quality product images
8. **Delivery**: Generated images sent back to user via Telegram

## Key Features

- **Conversational Brief Collection**: Natural language interaction through Telegram
- **Intelligent Persona Generation**: Creates detailed customer personas with demographics, psychographics, and preferences
- **AI-Powered Image Creation**: Generates product images tailored to specific personas
- **Automated Workflow**: End-to-end automation from brief to final deliverables
- **PostgreSQL Integration**: Persistent storage for campaign data and workflow triggers
- **Asynchronous Processing**: Handles long-running image generation tasks efficiently

## Generated Persona Structure

Each persona includes:
- **Demographics**: Age, gender, location, education, occupation, income, family status
- **Psychographics**: Lifestyle, values, personality traits, interests
- **Goals & Motivations**: Primary/secondary goals, motivators
- **Pain Points**: Customer challenges and concerns
- **Purchase Behavior**: Buying triggers, objections, decision-making style
- **Ad Preferences**: Preferred tone, visual style, CTA style

## Setup Requirements

- n8n instance with required integrations
- OpenAI API credentials
- Black Forest Labs API access
- PostgreSQL database
- Telegram Bot API token

## File Structure

- `brief.json` - Campaign brief collection workflow
- `persona-creative.json` - Persona generation and creative workflow
- `img-gen.json` - Image generation sub-workflow
- `README.md` - Project documentation

This system demonstrates advanced workflow automation combining multiple AI services to create a complete marketing automation pipeline.