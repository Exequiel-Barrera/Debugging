# Debugging

describe the issue i encountered?
 I was working through my korihi challenge when  i got to the part that i needed to write a new post,so then when i submitted the post through the blog app, the post content appeared in a way it was not supposed to; like a JSON object instead of just the text by itself, such as this example:" {"text":"doesnt work :("}" then i went to check one of the Hooks file; useCreatePost, and then the mutation i wrote before, which after doing few tries with different codes and asking my classmates for any idea what could be wrong, i got a clue from somebody who mentioned 2 lines of code were not like the ones she had, so i looked into those lines and did some changes , but it did cause another; i started sending empty body , regarding API was expecting " some message" 


describe the techniques i used for debugging

OBSERVING ERROR MESSAGE AND UI BEHAVIOR
After writing a new post on the blog and submitting this one  i notices the content was rendered as a JSON object instead of a text, which one was telling the data format that i was sending was incorrect.

Backtracking 
I traced the issue back to the custom react hook responsible for creating posts, so i did compare it to the similar hook ;"useReplyTo" so then notices useCreatePost was not handling input values correctly, since the request body sent to the API was an empty object instead of including the post text.

then Fixing and verifying the solution 
I updated the mutation fn to accept {text} parameter and send it correctly and with the right format in the request body. after making this change, i tested the feature several times to confirm it was ok. Post readable as plain text on the blog app
