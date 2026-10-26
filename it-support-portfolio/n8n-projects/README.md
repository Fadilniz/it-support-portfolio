# n8n projects — AIRA demo

I built these for AIRA, my side project. It is demo only. No paying clients yet.

I am not publishing the raw n8n files here. Those exports have real emails and credential references in them, so I am only writing descriptions for now.

## 1. Appointment booking
20 nodes. A webhook comes in, it checks availability, writes to Google Sheets and Google Calendar, sends a Gmail confirmation, and replies back.

The related workflows cover the full thing: book, check availability, update, cancel, and delete.

It was not perfect. Bookings sometimes timed out, and sometimes it updated the wrong row in Sheets. That is part of why I am writing this honestly.

## 2. Multi-tenant call concurrency
25 nodes, with Twilio and a lot of HTTP calls.

The idea is simple: when a lot of calls come in for different clients at the same time, you cannot just handle one and drop the rest. This routes by tenant, checks capacity, and if it is full it goes down an overflow path instead of dropping the call.

## 3. Call intake and emergency triage
11 nodes. A call comes in, it captures the info, sorts it by case type, checks the calendar, and there is an AI agent step in there.

The Emergency Triage file on its own is only 2 nodes. It is just a routing piece inside intake, not a full system. I do not want to make it sound bigger than it is.

## 4. RAG knowledge base
13 nodes, plus a memory workflow with Pinecone.

Google Drive triggers it, it loads documents, splits the text, turns it into embeddings with OpenAI, stores it in Pinecone, and then an AI agent answers by looking stuff up first.

So it is retrieval first, not just a prompt.
