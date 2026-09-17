---
license: apache-2.0
dataset_info:
  features:
  - name: video
    dtype: string
  - name: frames_response
    dtype: string
  - name: sliced_frames
    sequence: image
  splits:
  - name: train
    num_bytes: 524288000
    num_examples: 500
  download_size: 500000000
  dataset_size: 524288000
configs:
- config_name: default
  data_files:
  - split: train
    path: data/train-*
task_categories:
- video-classification
- image-to-text
- visual-question-answering
language:
- en
tags:
- gym
- fitness
- exercise-analysis
- video-understanding
- sports
pretty_name: Gym Exercise Video Analysis
size_categories:
- n<1K
---

# 🏋️‍♂️ Gym Exercise Video Analysis Dataset

**Gym Exercise Video Analysis** is a multimodal dataset designed for video-based action recognition, exercise form evaluation, and automated fitness coaching. It contains **500 detailed video instances** captured across diverse gym settings, complete with extracted frame sequences and comprehensive narrative analysis of each movement.

---

## 📊 Dataset Overview

* **Repository:** `prithivMLmods/Gym-Exercise-Video-Analysis`
* **Total Rows:** 500 samples
* **Splits:** `train` (500 rows)
* **Format:** Multimodal (Extracted Frame Sequences + Detailed Text Descriptions)
* **Domain:** Fitness, Weightlifting, Bodybuilding, Home & Commercial Gym Workouts

---

## 💡 Features & Schema

The dataset follows a structured schema combining visual frame sequences with granular step-by-step textual descriptions:

| Feature Name | Type | Description |
| :--- | :--- | :--- |
| `video` | `string` / `video` | Video file name or reference path. |
| `frames_response` | `string` | Detailed AI/Expert textual breakdown of the workout session, form, muscles targeted, and execution steps. |
| `sliced_frames` | `list[image]` | A list of keyframes (typically 5 sliced frames) representing the temporal progression of the movement. |

---

## 🏋️ Covered Exercises

The dataset covers a wide spectrum of compound and isolation gym exercises, including but not limited to:
- **Upper Body Pull:** Pull-ups, Lat Pulldowns, Inverted Rows, Cable Rows, Dumbbell/Barbell Rows, Bicep Curls (Dumbbell/Cable).
- **Upper Body Push:** Bench Press (Incline/Flat), Overhead Barbell Press, Seated Shoulder Press, Cable Chest Flys, Dips, Push-ups.
- **Lower Body & Core:** Barbell Squats, Romanian Deadlifts (RDL), Pistol Squats, Leg Extensions, Hanging Leg Raises, Russian Twists, Crunches.

---

## 📝 Sample Data Entry

Each entry includes a sequence of 5 sliced frames along with a rich textual analysis:

> **Example Description (`frames_response`):**
> *"The video captures an individual performing a Lat Pulldown. The person, dressed in athletic attire with a towel draped over their thighs for support, sits on a specialized reclining machine. Throughout the sequence, the movement targets the latissimus dorsi, engaging the lats, upper back, and biceps with controlled form."*

---

## 🚀 Quickstart Usage

### Using Hugging Face `datasets`

```python
from datasets import load_dataset

# Load the dataset directly from Hugging Face
dataset = load_dataset("prithivMLmods/Gym-Exercise-Video-Analysis")

# Inspect the first example
sample = dataset["train"][0]

print("Exercise Description:\n", sample["frames_response"])
print(f"Number of sliced frames: {len(sample['sliced_frames'])}")

# Display the first keyframe image
first_frame = sample["sliced_frames"][0]
first_frame.show()