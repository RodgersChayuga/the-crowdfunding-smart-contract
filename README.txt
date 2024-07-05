THE CROWDFUNDING SMART CONTRACT

This smart contract defines a crowd-funding campaign with features for contribution, refunding, and managing spending requests. Here's a breakdown of its functionalities:

1. Campaign Setup:

Defines a goal amount to be raised.
Sets a deadline for the campaign.
Tracks the campaign administrator (admin) and minimum contribution amount.

2. Contributions:

Allows users to contribute funds (payable in Ether) to the campaign.
Enforces a minimum contribution and checks if the deadline hasn't passed.
Keeps track of individual contributions per address in a mapping (contributors).
Increments the number of contributors when someone contributes for the first time.
Updates the total raised amount (raisedAmount).
Emits a ContributeEvent to record the contribution on the blockchain.

3. Refunds:

Allows contributors to claim refunds if the goal isn't reached by the deadline.
Ensures the deadline has passed and the goal wasn't met.
Transfers the contributor's amount back to their address.
Resets the contributor's contribution amount in the contributors mapping.

4. Spending Requests:

Defines a Request struct to store details like description, recipient address, amount, completion status, and number of voters.
Allows the admin to create spending requests using the createRequest function.
Tracks spending requests in a separate mapping (requests) using an index (numRequests) that starts from zero.

5. Voting on Requests:

Lets contributors vote on spending requests.
Requires the contributor to have contributed before voting.
Prevents users from voting multiple times on the same request.
Tracks votes per request and per contributor in the requests mapping.

6. Making Payments:

Only the admin can approve and pay for spending requests using makePayment.
Ensures the request isn't already completed and has received enough votes (more than half of contributors).
Transfers the requested amount to the recipient address.
Marks the request as completed in the requests mapping.
Emits a MakePaymentEvent to record the transaction.
Overall, this smart contract facilitates a crowd-funding campaign with transparency and control. Contributors can track their funds and vote on spending decisions, while the admin manages requests and ensures responsible use of the raised funds.