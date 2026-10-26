# Fadil Nizar — IT Support Portfolio

Hi, I'm Fadil. I live in Mississauga and I'm looking for my first IT job. I'm aiming for IT Support Tier 1, SaaS Technical Support, or Implementation / Onboarding work.

I made these projects in my lab to learn the actual work, not just theory. None of this is for real clients. All the people and data in here are fake.

## My projects

### 1. Zendesk ticket simulation
I worked 5 support tickets and marked them Solved. They are based on problems that actually happen on a POS, but the people in them are fake test users.

- POS terminal frozen mid-order
- Receipt printer offline
- POS login locked out
- Card reader failing
- Menu price wrong on POS vs menu board

For each one I wrote what was reported, what I checked, what fixed it or what I would escalate, and how urgent it was.

I want to grow this to 15-20 tickets. I have not done that part yet.

### 2. n8n appointment booking
I built this for AIRA, my side project. It is demo only. No paying clients yet.

It books appointments, checks availability, updates and cancels, and writes to Google Sheets and Google Calendar, then sends a Gmail confirmation.

It was not perfect. Bookings sometimes timed out, and sometimes it updated the wrong row in Sheets. I am not hiding that. I learned a lot from fixing those kinds of bugs.

### 3. Multi-tenant call concurrency
This one is about what happens when a lot of calls come in at once for different clients. Instead of dropping calls when it gets busy, it routes them and has an overflow path.

I built it with n8n, Twilio, and HTTP calls. 25 nodes in total.

### 4. Call intake and emergency triage
A caller comes in, the workflow captures the info, sorts it by case type, and checks the calendar. There is an AI agent step in there too.

The standalone Emergency Triage file is only 2 nodes. It is just a routing piece inside intake, not a full system on its own. I do not want to make it sound bigger than it is.

### 5. RAG knowledge base
I built a knowledge base that reads documents from Google Drive, splits them up, turns them into embeddings with OpenAI, stores them in Pinecone, and then an AI agent answers from those documents.

So it is not just a chatbot prompt. It actually looks stuff up first.

### 6. Entra user lifecycle — done Oct 26, 2026
I made a fake company called Northline HVAC. 12 fake people, 3 groups: Office, Technicians, Dispatch.

I did the full cycle with one fake user, Maya Chen:
- Joiner: I created her account and put her in Office
- Mover: I moved her from Office to Dispatch
- Password reset: I reset her password to a temp one
- Leaver: I blocked her sign-in and took her out of Dispatch

I left her account blocked, not deleted, so there is still a record.

Full write-up is in entra-user-lifecycle/README.md.

## What is not in here
I am not publishing my raw n8n files. Those exports still have real emails and credential references in them, even though there are no API keys in plain text. So I am only publishing descriptions for now. If I ever publish the files, I will clean them first.

No client names. No real customer data. No real coworkers.

## Contact
- GitHub: github.com/Fadilniz
- LinkedIn: linkedin.com/in/fadilnizar
- Email: fadil@aira.company
