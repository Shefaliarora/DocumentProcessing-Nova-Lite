# DocumentProcessing-Nova-Lite

I built a fully serverless AI-based document understanding pipeline that:
📄 Extracts unstructured text from invoices using Amazon Textract
🧠 Uses Amazon Nova Lite (via Bedrock) to intelligently convert raw text into structured JSON
📥 Automatically validates and stores that data into Amazon DynamoDB
📊 Making it ready for downstream analytics via Athena or QuickSight!

This use case is a great starting point for:
✅ Automating invoice processing
✅ Resume parsing
✅ Legal contract understanding
✅ Or any scenario where structured data is trapped in unstructured documents

💡 Built entirely with AWS managed services — no infrastructure to manage, highly scalable, and production-ready.

**Sequence of Steps**
Document Upload
PDF or image uploaded to S3 bucket (ai-documentintelligence-nova-demo)
Trigger Lambda Function
triggerTextractLambda reads file, calls Amazon Textract
Text Extraction
Textract extracts lines, forms, and tables
Invoke Nova via Bedrock
parseWithNovaLambda sends text to amazon.nova-lite-v1:0
Extracts structured fields (invoice_number, amount, dates, etc.)
Clean & Parse JSON
Lambda strips markdown formatting and validates JSON
Store in DynamoDB
validateAndStoreLambda stores final structured JSON in DocumentData table

