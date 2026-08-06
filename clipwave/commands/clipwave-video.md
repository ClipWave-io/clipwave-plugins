---
description: Generate a video clip with Clipwave from a prompt
---

Generate a video with Clipwave from this brief: $ARGUMENTS

Follow the `video-generation` skill:

1. Call `list_models` and choose a model that fits the brief. Use `t2v_id` for a
   prompt alone, `i2v_id` if the user supplied a starting image.
2. Tell the user which model you picked and why before submitting.
3. Submit with `media_forge_generate`, then poll `job_status` until completed.
4. Return the resulting video URL.

If Clipwave returns 401, follow the `setup` skill instead of retrying.
