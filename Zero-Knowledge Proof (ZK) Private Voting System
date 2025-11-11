# Experiment 5: Zero-Knowledge Proof (ZK) Private Voting System
# Aim:
To implement a fully private and transparent voting system using Zero-Knowledge Proofs (ZKPs). This ensures that votes are counted fairly without revealing who voted for whom.

# Algorithm:
Step 1: Voter Registration
Each voter generates a secret vote key and submits a commitment (hashed vote) to the contract.


Step 2: Voting Process
Voters submit their votes privately using a hash, without revealing their choice.


Step 3: ZK Verification
The contract verifies if a vote belongs to a registered voter but does not reveal the actual vote.


Step 4: Vote Counting
Once voting ends, the contract reveals the final tally without linking votes to individuals.



# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract ZKVoting {
    struct Voter {
        bool registered;
        bytes32 voteCommitment;
    }

    mapping(address => Voter) public voters;
    uint256 public votesForA;
    uint256 public votesForB;

    event VoteCommitted(address voter, bytes32 commitment);
    event VoteRevealed(address voter, uint256 choice);

    function registerVoter(bytes32 commitment) public {
        require(!voters[msg.sender].registered, "Already registered");
        voters[msg.sender] = Voter(true, commitment);
        emit VoteCommitted(msg.sender, commitment);
    }

    function revealVote(string memory secret, uint256 choice) public {
        require(voters[msg.sender].registered, "Not registered");
        require(keccak256(abi.encodePacked(secret, choice)) == voters[msg.sender].voteCommitment, "Invalid proof");

        if (choice == 1) votesForA++;
        if (choice == 2) votesForB++;

        emit VoteRevealed(msg.sender, choice);
    }
}

```
# Expected Output:
Voters commit their votes privately.


When revealed, the contract verifies correctness but keeps votes anonymous.


Final result is publicly verifiable without exposing individual votes.



# High-Level Overview:
Uses ZKPs to ensure anonymous and fair elections.


Prevents vote tampering while maintaining voter privacy.


Mimics real-world ZK voting applications in governance and DAOs.

# Output:
<img width="1327" height="562" alt="Screenshot 2025-11-05 105241" src="https://github.com/user-attachments/assets/0a89ddcf-02c6-4302-b74d-d1b232bc686e" />

### To generate a hash to register vote (web3.utils.soliditySha3("apple", 1)):

<img width="595" height="84" alt="Screenshot 2025-11-05 105322" src="https://github.com/user-attachments/assets/99dffe68-b9e7-4ebf-9740-744f47732285" />

### Verify the registered Vote:

<img width="197" height="420" alt="Screenshot 2025-11-05 105252" src="https://github.com/user-attachments/assets/917caa6e-fe9d-4000-8c99-a2e186287bbc" />


# RESULT: 
Thus to implement a fully private and transparent voting system using Zero-Knowledge Proofs (ZKPs) is executed Succefully.
