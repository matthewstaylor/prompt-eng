![GenI-Banner](https://github.com/genilab-fau/genial-fau.github.io/blob/8f1a2d3523f879e1082918c7bba19553cb6e7212/images/geni-lab-banner.png?raw=true)

# Pick-up Basketball MVP

If you need to know the most valuable player in your basketball group to pick them for your team, this service aims to do that through analysis of core concepts of what makes the best player on the court.

* Authors: Matthew Taylor
* Academic Supervisor: [Dr. Fernando Koch](http://www.fernandokoch.me)

  
# Research Question 

* Being awarded the title of MVP in a sports game carries weight, especially in a pick-up basketball game. Being in a space where many players are waiting their turn to ball, being known as the best player can go a long way if you like to play often. Other players are much more likely to pick you for their team if you are known as the MVP.

* Many arguments can be made as to what qualities or traits define a most valuable player. Based on my own knowledge, I would say some core traits of an MVP on the public basketball court include -
  * Scoring ability - scoring often and consistently on attempts
  * Trustworthiness - decisions are trusted and respected by your teammates
  * Playing defense - making an effort when playing defense 

* My research aims to utilize generative AI prompt techniques to help in defining requirements for a service to determine an MVP based on recorded players and their player reports with statistics on playing ability and personality on the court. 

## Arguments

#### What is already known about this topic

* One could consult with a professional basketball expert who can analyze historical stats of many winning players and teams over the decades of the NBA. Knowledge from a career professional, subject-matter expert could be trusted and leveraged in making the determination themselves.
* Many individual opinions could differ on the criteria for designation as MVP, introducing potential biases to the determination of such a player. 
* Since basketball has been played for over 100 years, patterns of MVPs in basketball players playing at a variety of skill levels can be acknowledged and presented in the decision-making.

#### What this research is exploring

* I employ the Chain of Thought and Zero-Shot LLM prompting techniques.
* I am building a service to help pick MVP players to play pick-up games with at basketball courts.
* I am exploring using many styles of prompting to generate a service that utilizes multiple perspectives from myself and the LLM.

#### Implications for practice

<!-- Free-format; use the topics that are applicable to your exploration  -->

* It will be easier to play with a diverse set of players and determine an MVP from one's own perspective.
* It will optimize the process of determining the MVP at a basketball court, so one can single this person out as a good teammate to choose.
* I will better understand how to define an MVP-caliber player at basketball courts.

# Research Method

To conduct this research process, I intend to utilize prompt engineering techniques to help define examples of MVP pick-up 
players as well as develop player data input ideas.

Prompt engineering techniques of interest include Chain of Thought and Zero-Shot.

Chain of Thought will be employed for requirements analysis by prompting the LLM with my own perceptions of a pick-up basketball MVP, 
and asking for examples of players that might embody MVP traits. I will provide a few diverse examples to effectively prompt the LLM in this fashion.
I expect the results will help develop an image of MVPs outside the scope of my own imagination.

Zero-Shot will be utilized for requirements analysis by "picking the brain" of the LLM, by learning from its own training knowledge 
related to MVP pick-up basketball players. I will prompt the LLM with a general question related to being an MVP, and rely on its own knowledge to answer.
I expect the results could help define traits to look for in MVPs.

Combining the results of the LLM responses with my own knowledge of the pick-up games, I plan to define a system utilizing multiple perspectives for clarity.

# Results

### Chain of Thought
```
CHAIN_OF_THOUGHT = "In a game of pick-up basketball, a player is shooting consistently well, hitting shots, has great " \
              "rapport with many people at the gym, and plays active defense, really trying to block shots and force " \
              "turnovers. These are MVP qualities of a pick-up basketball player." \
              "In another game of pick-up basketball, another player has scored many baskets, outnumbering the other " \
              "players by 20 points. However this player does not care about playing defense so the other pick-up " \
              "players on his team suffer on defense. These are not MVP qualities." \
              "Now present some example pick-up basketball players that would embody an MVP."
    PROMPT = CHAIN_OF_THOUGHT
    payload = create_payload(
        target="ollama",
        model="llama3.2:latest",
        prompt=PROMPT,
        temperature=1.0,
        num_ctx=100,
        num_predict=100)
```
```
Here are some examples of pick-up basketball players who embody MVP (Most Valuable Player) qualities:

1. **The Scorer**: "Lightning" Lance, a 6'5" point guard with incredible shooting ability and athleticism. He can score from anywhere on the court, and his ability to draw fouls and sink free throws at will makes him nearly unstoppable.
2. **The Playmaker**: "Q" Qureshi, a 6'8" forward with exceptional court vision
```

Considering the results of Chain of Thought, the LLM responded with two examples of players that embody MVP qualities.

Providing nicknames, player height, and a one-liner description of each player is helpful in looking at players from a high-level.
This allows my requirements analysis examples to look for in players. Previously I did not consider player height, but after 
analyzing the Chain of Thought response, I realize that height is a huge importance as well, as players would be naturally closer to the net to score.

While I find the examples helpful for a high-level perspective, I expected the LLM to respond with more details given the detail of the presented chain-of-thought.
For example, "The Playmaker" has very little description outside of having court vision.
"The Scorer" does have more detail, but I expected more granular traits like I presented in the prompt.

I can take these example players going forward in requirements analysis.

### Zero-Shot

```
ZERO_SHOT = "What traits or qualities of a regular player in pick-up basketball at a local gym would define a " \
                "pick-up basketball MVP?"

    PROMPT = ZERO_SHOT
    payload = create_payload(
        target="ollama",
        model="llama3.2:latest",
        prompt=PROMPT,
        temperature=1.0,
        num_ctx=100,
        num_predict=100)
```

```
A pick-up basketball MVP (Most Valuable Player) at a local gym might possess some unique traits and qualities that set them apart from the rest. Here are some possible characteristics:

1. **Adaptability**: A good pick-up player can adjust to different team dynamics, playing styles, and opponents quickly. They can pivot their game plan mid-match if needed.
2. **High basketball IQ**: Understanding of the game's strategies, rules, and nuances helps a pick-up player make smart decisions on
```

Reviewing the interaction regarding Zero-Shot prompting, the LLM responded with MVP qualities and detailed explanations for each of them.

The qualities that resulted from the LLM's trained knowledge are detailed and highlight traits I did acknowledge going into the service design.
Adaptability is a huge advantage for any player, and being highly adaptable should also be a huge trait associated with pick-up basketball MVP, 
as you never know who one will play with in a true pick-up!
If a player can play with most people and any given set of them as a team, the player can use this to help lead their team to success while performing well individually.

I am satisfied with the results of Zero-Shot, and look to consider measuring these traits in my requirements analysis.


# Further research

Further research on the pick-up basketball MVP subject could be conducted. As more prompt engineering techniques are available outside 
the scope of ones chosen for this research, these could be experimented with to further gain more knowledge for the requirements. 
More specific prompt engineering techniques can also be created for use in this case, such as an LLM with many data points focusing on basketball.
