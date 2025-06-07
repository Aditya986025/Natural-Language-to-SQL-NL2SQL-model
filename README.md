# Natural-Language-to-SQL-NL2SQL-model
This project evaluates a Natural Language to SQL (NL2SQL) model using the transformer model `tscholak/cxmefzzi` from Hugging Face. The aim is to determine how accurately the model can translate natural language questions into executable SQL queries based on a given schema.... 


Step 1 : 
![Screenshot 2025-05-23 121519](https://github.com/user-attachments/assets/a1aed44f-ede2-4d57-b51d-e1c0414ac0c6)


Step 2 :
![Screenshot 2025-05-23 121534](https://github.com/user-attachments/assets/cd23acd0-f9d0-4eb5-a7e5-3438528bf7a2)



![Screenshot 2025-05-23 121556](https://github.com/user-attachments/assets/92af6811-bd63-4540-9f56-d5d332665c95)


Final Result : 
![Screenshot 2025-05-23 121607](https://github.com/user-attachments/assets/a2c149d5-ee9d-4095-b0eb-3b78ccbdb703)


2. Approach
The evaluation followed these steps:
- Loaded the pretrained tokenizer and model.
- Serialized input as: '<natural language query> | <db_id> | <schema>'.
- Used an in-memory SQLite database with a table `customers`.
- Inserted sample customer records including cities such as New York and Mumbai.
- Cleaned the model output by removing irrelevant prefixes (e.g., 'customers_db |').
3. Evaluation Metrics
- Exact Match Accuracy: Checks if the predicted SQL exactly matches the expected SQL.
- Execution Accuracy: Compares the result of executing both SQLs to verify equivalence.
4. Sample Test Cases
Three representative test cases were used:
1. NL: What is the total number of customers from New York?
   - Expected: SELECT COUNT(*) FROM customers WHERE city = 'new york';
   - Predicted: SELECT COUNT(*) FROM customers WHERE city = 'new york';
2. NL: List the names of customers older than 30.
   - Expected: SELECT name FROM customers WHERE age > 30;
   - Predicted: SELECT name FROM customers WHERE age > 30;
3. NL: How many customers live in Mumbai?
   - Expected: SELECT COUNT(*) FROM customers WHERE city = 'mumbai';
   - Predicted: SELECT COUNT(*) FROM customers WHERE city = 'mumbai';
5. Results
- Exact Match Accuracy: 100%
- Execution Accuracy: 100%
The model performed accurately across all test cases. Cleaning the output was crucial to ensure the predictions were in a proper executable format.
6. Conclusion
The `tscholak/cxmefzzi` NL2SQL model shows strong performance on structured queries for simple database schemas. With some preprocessing and output formatting, the model can be reliably used for semantic SQL generation..

finally done
