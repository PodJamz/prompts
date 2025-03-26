# Photorealistic Portrait Generator

## Description
A prompt template for generating highly detailed, photorealistic portraits of people with specific characteristics, environments, and moods.

## Target Models
- DALL-E 3
- Midjourney v5/v6
- Stable Diffusion XL

## The Prompt
```
Create a photorealistic portrait of [PERSON DESCRIPTION] in [ENVIRONMENT], [ACTION/POSE]. [LIGHTING] lighting. [EMOTION/EXPRESSION] expression. [CAMERA DETAILS]. [STYLE REFERENCE].

--ar 2:3 --v 5.2 --q 2 --s 750
```

## Parameter Explanation
- **PERSON DESCRIPTION**: Age, gender, ethnicity, notable features, clothing, etc.
- **ENVIRONMENT**: Indoor/outdoor location, setting details
- **ACTION/POSE**: What the person is doing, how they're positioned
- **LIGHTING**: Type of lighting (natural, studio, dramatic, etc.)
- **EMOTION/EXPRESSION**: The mood or feeling conveyed
- **CAMERA DETAILS**: Focal length, perspective, framing
- **STYLE REFERENCE**: Photography style or photographer reference
- **Parameters**: Aspect ratio, model version, quality, stylization (for Midjourney)

## Examples

### Example 1:
```
Create a photorealistic portrait of a 68-year-old Japanese fisherman with weathered skin and salt-and-pepper beard in a small wooden boat at dawn, mending nets. Golden hour lighting casting long shadows. Contemplative, peaceful expression. Shot on Canon 5D with 85mm lens, shallow depth of field. Style reminiscent of Steve McCurry's environmental portraits.

--ar 4:5 --v 5.2 --q 2 --s 750
```

### Example 2:
```
Create a photorealistic portrait of a 30-year-old African American female scientist in a modern laboratory, examining a test tube. Cool blue lighting from overhead LEDs reflecting off glass surfaces. Focused, determined expression. Wide angle shot showing environment, professional documentary style. Similar to National Geographic photography.

--ar 3:2 --v 5.2 --q 2 --s 750
```

## Tips
- Be very specific about facial features, age, and clothing
- Include details about the environment to ground the portrait
- Lighting dramatically affects the mood - be specific
- Reference well-known photographers or photography styles for better results
- For Midjourney, add the parameters at the end of your prompt
- For more photorealism, avoid fantastical or impossible elements
- Sometimes adding "photorealistic, 4K, detailed" can enhance quality 