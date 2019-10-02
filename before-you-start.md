With just an hour or two of work up-front, it's possible to avoid many of the reasons stories become frustrating and unpleasant. Don't get your PRs kicked back; do your work up front.

1. **Get All the Answers.** Product and UX's job is to help you resolve all the edge cases. Make sure you understand:
  * What to do if operations fail (bad user input, bad API response, bad login state, etc.)
  * What device types you need to make this work on
  * Confirm that any changed text, links, etc., is actually meant to change and not a typo
2. **Assess ways to do the ticket.** Read the code and understand how things work in the module (if you're developing something from scratch, find similar things and understand how they work). Outline multiple options in writing, in ticket comments. It may help to draw pictures at this stage.
3. **Consult a Colleague.** Ask someone what they think of your approaches. Senior and Principal Engineers are specifically paid to do these things, so don't be shy about asking them. Agree on a preferred approach.
4. **Go to a Domain Expert.** If another team often works with this kind of code , then reach out to validate your approach.
5. **Document the Chosen Approach.** Describe the approach in the ticket comments. This comment doesn't need to be all-encompassing, but, if someone finds the ticket in 8 months and needs to do the same thing, they should be able to get a good start from your comment.


### FAQ

#### Do I need to do this every time?

No, it's certainly too much effort for 1-point tickets, but the effort's worth it for >=3-point tickets.

#### Don't you trust me to plan my story on my own?

Sure, and we also trust you to execute the plan and write code. But we also have code review, because we're all, together, smarter than any one of us, individually. Think of the above as "idea review".

#### I don't want to ask dumb questions of Senior Engineers, that makes me feel dumb.

Answering those questions is literally in their job description, and they're literally evaluated on how well (and positively!) they answer them. You should never be made to feel dumb.

#### So I can ask any dumb question, then?

Ask your best question. Do enough research that you're comfortable you have a specific question that, when answered, will lead you forward. Some advice on asking good questions: [1](https://stackoverflow.com/help/how-to-ask) [2](https://medium.com/@dan_abramov/asking-good-questions-421f08ee7e5c), [3](https://medium.com/@gordon_zhu/how-to-be-great-at-asking-questions-e37be04d0603), [4](http://www.catb.org/~esr/faqs/smart-questions.html), [5](https://codeblog.jonskeet.uk/2012/11/24/stack-overflow-question-checklist/).

Your best question probably expresses less understanding of a topic than a subject matter expert would have. If you knew all that SME knew, you wouldn't have a question. Don't worry that you know less.

#### What do I do if I get an answer?

Document it! In the Comments, if it's trivial; if you think it would be useful to other people, in the wiki. If you're not sure, you have your own page on the wiki, so put it there. Documenting things you learn helps you not have to ask the same questions again and again, which makes you faster and happier. Soon, you'll be the expert!

#### That's a lot of documentation!

Would you rather write a few comments or have people keep asking you what's going on? Thought so.
