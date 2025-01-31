# speculative-editing
Simple yet very effective technique for optimizing LLM inference when rewriting code. 
Goal: Much faster variant of speculative decoding specifically for rewriting code, code editing and code gen.

# Why?
Speculative Decoding is a technique for general acceleration of the LLM inference, created to target the problem of large autoregressive models like Transformers being slow (to decode K tokens, model needs to do K forward passes).  It allows to generate tokens much faster, without changing the output distribution nor further fine-tuning, by using a smaller, drafter model to speculative tokens, much quicker that can later be verified by the main model in one forward pass.

In code rewriting/editing tasks one can notice that often only a very small subset of the whole codebase needs to be changed, although the model still has to usually go through all of it to understand what needs to be changed.

# So what's the idea with Speculative Editing? 
Basically - instead of using a smaller model to draft the candidate tokens, we may use the draft we need to edit itself and verify it step-by-step using the larger model. Which eliminates the need to edit the code in such very auto-regressive and sequential manner.

I have initial validation on it from Cursor, which I suppose uses it on fast-apply in their interface. I suppose the technique originates from them, tho I didn't find any specific documentation or open implementatation of it, despite how effective and interesting it may be...

# My work is in progress
I currently work on speculative editing along some other projects I do, currently exploring and experimenting in the notebook - 
