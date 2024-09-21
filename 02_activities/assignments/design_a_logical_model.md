# Assignment 1: Design a Logical Model

## Question 1
Create a logical model for a small bookstore. 📚

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).

## Question 2
We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.

## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Bonus: Are there privacy implications to this, why or why not?
```
Retaining Address Changes (Type 2 SCD)
This approach tracks every change to a customer’s address, retaining historical information. Each address change creates a new record with start and end dates to define the time period when the address was valid.

Yes, there are privacy implications, particularly with the Type 2 approach where historical addresses are retained
Privacy Risk: Storing historical addresses poses a higher privacy risk. If this data is compromised or misused, it could reveal personal location history, which could be sensitive (e.g., if a customer moved to escape a harmful situation).
Mitigation: The store should have strong data protection policies and compliance with data privacy regulations (e.g., GDPR, CCPA). Implementing encryption for sensitive data and offering customers the option to request deletion of old addresses may help mitigate this risk.
```

## Question 4
Review the AdventureWorks Schema [here](https://i.stack.imgur.com/LMu4W.gif)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
yes, they included the PK and FK
and The AdventureWorks schema is highly normalized. There are separate tables for Address

I would consider changing the way addresses are handled in the bookstore ERD if the business needs expand over time. Here’s why:

Multiple Addresses: If the bookstore starts offering shipping options, a customer may need to maintain separate billing and shipping addresses. Storing these in a separate Address table (like in AdventureWorks) would allow the flexibility to manage multiple addresses per customer.

Normalization and Data Integrity: Normalizing addresses into a separate table reduces data duplication. For example, if many customers live in the same city or have the same ZIP code, storing this information separately avoids redundancy. It also ensures that address data can be updated in one place without affecting multiple records.

Scalability: As the business grows, having a more scalable solution for addresses would be helpful. If you eventually need to track addresses for employees (for HR purposes), suppliers, or other entities, a separate Address table that links to multiple tables makes the database design more flexible and easier to maintain.
```

# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `September 28, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-4-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
