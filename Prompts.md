There are different kinds of prompt formats depending on the type of model being used and the task requirements. In the context of multimodal models like LLaVA-NeXT, prompts are often structured to integrate multiple types of inputs (e.g., text, video, images) and to guide the model's behavior. Here are some common formats and their variations:

1. Instruction-Based Prompts (Instruction + Content)
This format pairs an instruction with the input content (e.g., text, video). It is commonly used in instruction-tuned models.

Example
conversations = [<br>
    [{
        "role": "user",
        "instruction": instruction,  # General instruction for the task
        "content": [
            {"type": "text", "text": line},  # Text input for context
            {"type": "video"}               # Video input
        ]
    }] for line in lines
]

When to Use
When you need to clarify how the model should process and respond to the input.
When the task requires processing multiple modalities (e.g., text + video).
2. Chat-Based Prompts (Role-Based Conversations)
In this format, inputs are structured as a conversation between a "user" and an "assistant."

Example
conversations = [
    {
        "role": "user",
        "content": "Describe the main events in this video."
    },
    {
        "role": "assistant",
        "content": None  # Model will generate the response
    }
]
When to Use
For tasks that simulate a conversational interface.
For models fine-tuned on dialogue-like datasets.
3. Multi-Modal Content with Embedded Metadata
This format includes metadata alongside the input, which can provide additional context or specify the input type explicitly.

Example
prompts = [
    {
        "role": "user",
        "instruction": "Analyze the given video and answer the question.",
        "content": [
            {"type": "text", "text": "What is happening in the video?"},
            {"type": "video", "url": "path/to/video.mp4"}  # Specify video location
        ],
        "metadata": {
            "frame_count": 64,
            "duration": "00:02:30"
        }
    }
]
When to Use
When the task involves complex inputs with detailed metadata.
For structured processing of input with additional information.
4. Sequential Task Prompts
This format is used for tasks where the model needs to process inputs step-by-step, often with a sequence of instructions.

Example
prompts = [
    {
        "role": "user",
        "instruction": "Step 1: Analyze the video. Step 2: Answer the question.",
        "content": [
            {"type": "video", "data": video_frames},
            {"type": "text", "text": "Is the person wearing a helmet?"}
        ]
    }
]
When to Use
When you want to break down tasks into steps.
For multi-step reasoning or evaluation tasks.
5. Context-Aware Prompts
This format provides a conversational history or previous context alongside the new query.

Example
conversations = [
    {"role": "user", "content": "What is happening in the video?"},
    {"role": "assistant", "content": "The video shows a person walking in a park."},
    {"role": "user", "content": "Are there any animals visible in the video?"}
]
When to Use
When the model needs context from prior interactions.
For dialogue or follow-up questions.
6. Task-Specific Prompts
These prompts are tailored for specific tasks like classification, summarization, or generation.

Example for Classification
prompts = [
    {
        "role": "user",
        "instruction": "Classify the actions visible in the video.",
        "content": [
            {"type": "video", "data": video_frames}
        ],
        "options": ["Walking", "Running", "Standing"]
    }
]
Example for Summarization
prompts = [
    {
        "role": "user",
        "instruction": "Summarize the events in the video.",
        "content": [
            {"type": "text", "text": "Summarize the video below:"},
            {"type": "video"}
        ]
    }
]
When to Use
For specialized tasks where the format aligns with the task's requirements.
7. Open-Ended Prompts
This format provides minimal structure and allows the model to generate free-form responses.

Example
prompts = [
    {
        "role": "user",
        "content": "Describe everything you observe in the video."
    }
]
When to Use
For exploratory tasks or when detailed responses are needed without strict guidance.
8. Instruction-Only Prompts
In this format, the instruction itself acts as the primary guide for the model.

Example
prompts = [
    {
        "instruction": "Watch the video and list all the objects visible."
    }
]
When to Use
For straightforward tasks with a single type of input.
9. Multiple Choice Prompts
This format provides the model with specific options for its output.

Example
prompts = [
    {
        "role": "user",
        "instruction": "What is the activity happening in the video?",
        "content": [
            {"type": "video", "data": video_frames}
        ],
        "choices": ["Running", "Walking", "Cycling"]
    }
]
When to Use
For classification or selection tasks.
10. Hybrid Prompts
Combines multiple types of input (e.g., video, text, images) in a flexible structure.

Example
prompts = [
    {
        "role": "user",
        "instruction": "Analyze the video and the accompanying text to answer the question.",
        "content": [
            {"type": "video", "data": video_frames},
            {"type": "text", "text": "Does the person appear to be injured?"}
        ]
    }
]
When to Use
For tasks requiring multimodal reasoning across text, video, and other modalities.
Choosing a Format
Use instruction-based prompts for clear task guidance.
Use context-aware or chat-based formats for conversational or sequential tasks.
Use task-specific prompts for focused tasks like classification, summarization, or open-ended reasoning.
Let me know if you'd like help structuring prompts for your specific use case!
