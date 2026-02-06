# Debugging

Describe the issue i encountered?
 I was working through my korihi challenge when  i got to the part that i needed to write a new post,so then when i submitted the post through the blog app, the post content appeared in a way it was not supposed to; like a JSON object instead of just the text by itself, such as this example:" {"text":"doesnt work :("}" then i went to check one of the Hooks file; useCreatePost, and then the mutation i wrote before, which after doing few tries with different codes and asking my classmates for any idea what could be wrong, i got a clue from somebody who mentioned 2 lines of code were not like the ones she had, so i looked into those lines and did some changes , but it did cause another; i started sending empty body , regarding API was expecting " some message" 


describe the techniques i used for debugging

OBSERVING ERROR MESSAGE AND UI BEHAVIOR
After writing a new post on the blog and submitting this one  i notices the content was rendered as a JSON object instead of a text, which one was telling the data format that i was sending was incorrect.

Backtracking 
I traced the issue back to the custom react hook responsible for creating posts, so i did compare it to the similar hook ;"useReplyTo" so then notices useCreatePost was not handling input values correctly, since the request body sent to the API was an empty object instead of including the post text.

then Fixing and verifying the solution 
I updated the mutation fn to accept {text} parameter and send it correctly and with the right format in the request body. after making this change, i tested the feature several times to confirm it was ok. Post readable as plain text on the blog app





Debugging Collaboratively 

When we first started coding the "Guess the image" game , the submit the answer button it was not doing its job when we were clicking it. There was no error we could in the UI, and the game state did not update, even though button was rendering and clickable.


Debugging techniques we used as a group.

-Add Console logging to inspect the behavior when we were clicking the button

As a group, we decided to first confirm wether the click handler was being trigerred at all, so we added console.log() statements inside the submit handler to check if; 

 *function was being called
 *Wether guessImage and userGuess had values at runtime.
  which as a result it did help us to see that the function was being called , but the guessImage was sometimes "null", causing the function to exit early

  - Checking components state and React hooks.

  We reviewed the component together and noticed that:
  * guessImage was only set when the start game button was clicked
  *the submit  loggic depended on guessImage being defined 
  so then we realised the issue was caused by state not being initialised correctly before submission, which it led us to : 

  - confirm the order of user actions
  -add guard clauses and better state resets when starting a new game 

  FOR REFACTORING LOGIC PLACEMENT

  At the beginning some logic( even the hint related code) was placed inside the submit handler, which made the flow harde to reason about . 

  So then as group we discussed separting concerms, moving that reusable logic into their own function making sure the submit handler was only doing and handling validation and scoring


  IN WHICH WAY THIS DEBUGGING WAS COLLABORATIVE

  The debugging process was collaborative because;

  - we discussed possible cause together before changing some code
  - some of us give some pieces of ideas checking different areas( state,hooks, Event handlers)
  -We checked the console output together to interpret what the app was actually doing 
  - we agreed on changes before refactoring to avoid introducing new possible bugs