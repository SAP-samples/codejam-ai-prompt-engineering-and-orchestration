# Exercise 01 - Understand the Document Grounding Pipeline

_Estimated Time: **05 min**_

In this exercise, you will learn what a document grounding pipeline is. This pipeline will pull a document from an S3 bucket on AWS, chunk it, vectorize it, and store it in a central SAP HANA Cloud vector engine.

## Table of Contents

- [Exercise 01 - Understand the Document Grounding Pipeline](#exercise-01---understand-the-document-grounding-pipeline)
- [The Document Grounding Pipeline](#the-document-grounding-pipeline)
- [Summary](#summary)
  - [Questions for Discussion](#questions-for-discussion)
- [Further Reading](#further-reading)

## The Document Grounding Pipeline

For this workshop, the S3 bucket is provided through the SAP Business Technology Platform Document Store service. The document was already uploaded to the document store on BTP. To pull the document from the document store, a secret is needed to properly authenticate against the document store. The secret was also pre-configured to keep the exercise concise and focused on the task at hand.

The Document Grounding service, as part of the grounding pipeline on SAP AI Core, is a great tool to simplify the grounding process of a contextual document for an orchestrated Retrieval Augmented Generation flow.

It automates the chunking and vectorization through a vector embedding process and stores these vector embeddings. Another benefit is that you don't need your own SAP HANA Cloud instance to utilize the vector engine. It uses a central SAP-hosted instance, which assigns a tenant to you where your vector embeddings are stored.  
Through that approach, you can save on provisioning your own SAP HANA Cloud instance if you only want to use the vector engine feature.

The chunking is currently not configurable and uses a default chunking setting, where the chunk size and parameters are set to divide the contextual document by section.

> NOTE: The following steps are already done for this workshop. Please do not follow the steps; they are just for your understanding!

Using the **Grounding Management** on SAP AI Launchpad, you can simply create the pipeline.

![grounding-pipeline-creation](./assets/create-grounding-pipeline-01.png)

As you can see, you simply define the **Document Store Type**—in our case, the **S3** bucket—and select the generic secret for authorization and authentication.

After the creation of the pipeline, the service will pull the documents, vectorize them, and store them in the vector engine.

![grounding-pipeline-result](./assets/create-grounding-pipeline-03.png)

## Summary

At this point, you have understood what the document grounding pipeline is and how it consumes an S3 bucket on AWS.

### Questions for Discussion

1. Can you currently configure the chunking parameters?
<details><summary>Answer</summary>
   No, at this point it is not possible to configure the chunking parameters for the document chunking. It applies a default chunking to prepare the contextual document for vectorization.
</details>

2. What information can you see when navigating into the detail screen of the data repository?
<details><summary>Answer</summary>
    You can inspect the chunks and the metadata. You can also search for specific chunks if you want to.
</details>

## Further Reading

- [Generative AI Hub on SAP AI Core - Help Portal (Documentation)](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide/generative-ai-hub-in-sap-ai-core-7db524ee75e74bf8b50c167951fe34a5)
- [Out-of-the-Box Document Grounding in SAP AI Core: RAG with SAP Help Portal](https://community.sap.com/t5/technology-blog-posts-by-sap/out-of-the-box-document-grounding-in-sap-ai-core-rag-with-sap-help-portal/ba-p/14076473)
- [Document Grounding in SAP AI Core: RAG with AWS S3 via Object Store Service on SAP BTP](https://community.sap.com/t5/technology-blog-posts-by-sap/document-grounding-in-sap-ai-core-rag-with-aws-s3-via-object-store-service/ba-p/14078294)
- [SAP Business Accelerator Hub - Grounding API](https://api.sap.com/api/DOCUMENT_GROUNDING_API/overview)

---

[Next exercise](../02-create-prompt-template/readme.md)
