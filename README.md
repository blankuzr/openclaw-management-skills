# openclaw-management-skills
A set of skills for loading into openclaw installations. Skill set focuses on openclaw configuration and management, and informs agents being run in openclaw about their setup and current documentation.


## How do I use this?
Put this anywhere on your box running openclaw where you are comfortable with openclaw agents being able to read from. 
In your openclaw.json config file, add this snippet to your `skills: {}` section

```
load: {
      extraDirs: ["~/<your-path-to-this-pack>/openclaw-management-skills/skills"],
      watch: true
    }

```
Or, you can save these skills to your `~/openclaw/skills` folder. 
If you run multiple agents and want these skills isolated to a specific agent, place the skills pack
in the per-agent skills folder: `~/.openclaw/<specific-agent-workspace>/skills`

Then restart the gateway

```
openclaw gateway restart
```

## Why did I make this?
### Models in openclaw dont know themselves (their openclaw state-of-existence) too well (unless using a larger more expensive model).
Model hopping / fallbacks can create instances where the agent no longer understands what it is doing to it's openclaw configuration. A local skills pack that details how to utilize openclaw configuration / parameters based on the latest online openclaw documentation can help LLMs assist the user more effectively when making changes / implmenting new tools/plugins into their openclaw system.

## How did I make this?
I asked gpt 5.2 with thinking cap on to go read and itemize the openclaw documentation and github source code. With this information I made gpt5.2 create a series of skills for managing openclaw setups.

## What was my first use case for this?
Once loaded into my openclaw, I use this + the skill creator skill to have my openclaw LLM make more skills / tools for me to use with my various plugins. I have found editing the config file to be easier as well. 

## Note:
The skills include urls to the openclaw documentation. 
If your openclaw agent accessing these skills does not have web browsing enabled (there are a few ways to go about this), they will not be able to utilize those urls, and will be limited to the details in the SKILL.md file (which is still plenty). 

