import { GoogleGenAI } from "@google/genai";

const ai = new GoogleGenAI({ apiKey: process.env.GEMINI_API_KEY || "" });

export async function humanizeText(text: string, tone: string, intensity: string) {
  if (!text.trim()) return "";

  const prompt = `You are a world-class editorial precision humanizer. Your task is to rewrite the provided AI-generated text to sound more human, natural, and engaging. 

Tone: ${tone}
Intensity: ${intensity} (Subtle means minor tweaks, Deep means significant restructuring for maximum human feel)

Input Text:
"${text}"

Output only the humanized text. Do not include any explanations or meta-talk.`;

  try {
    const response = await ai.models.generateContent({
      model: "gemini-3-flash-preview",
      contents: prompt,
    });

    return response.text || "Failed to generate humanized text.";
  } catch (error) {
    console.error("Gemini Humanization Error:", error);
    return "An error occurred while humanizing your text. Please check your API key and try again.";
  }
}
