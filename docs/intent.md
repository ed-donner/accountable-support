# Intent: Accountable Support

## Problem

The business behind Accountable builds and supports software and IT systems for small and mid-sized companies: booking systems, online ordering, patient portals, networks and support plans. Its customers report problems by email and phone, and the support team keeps track in a shared inbox and a spreadsheet. Nobody can see which tickets are waiting, which are late, what a customer was told last, or whether customers are happy with the answers.

## Proposed outcome

Accountable Support is a ticket system for that support team, a companion app to Accountable in the same suite. It should feel sharp, modern and professional, in the same spirit as Accountable, and be a pleasure to use every day.

This first version runs on one computer with no sign-in. The support team is four people with made-up names, and every ticket is assigned to one of them or to nobody yet. A reply or note is written as the ticket's assignee.

### A ticket

A ticket has a number, a subject, the customer who raised it (a contact at one of the customer organizations), a priority (Low, Normal, High or Urgent), a status (New, Open, Waiting on customer or Solved), an assignee, and when it was created, first answered and solved. New tickets are added by the team, on behalf of the customer who emailed or phoned.

### The six features

1. **The foundation.** The app's skeleton: the layout and navigation, the database, the sample data, the commands in `docs/TECH_STACK.md`, the tests and CI. The ticket list, the landing page, with a search box over subjects and customers, filters by status, priority, customer organization and assignee, columns you can sort by, and a way to add a new ticket.
2. **Ticket detail.** Open a ticket to see the conversation, oldest first: the customer's first message, the team's replies, the customer's answers, internal notes (which only the team sees, shown differently) and an entry for every change of status, priority or assignee. From the ticket you can reply, add an internal note, record the customer's answer, and change its status, priority or assignee. The first reply to the customer sets when the ticket was first answered; a note doesn't.
3. **SLA targets.** Each priority has a target for the first reply and a target for solving the ticket: Urgent 1 hour and 4 hours, High 4 hours and 1 day, Normal 8 hours and 3 days, Low 1 day and 1 week. The clocks run in calendar hours from when the ticket was created and don't pause. The list and the ticket show the time left on each target, a ticket close to a target is marked, and a ticket past one is flagged as breached. The ticket list can be filtered to breached tickets.
4. **A knowledge base.** Help articles with a title, a category and a body, which the team writes and edits. The knowledge base has its own page with search. From a ticket, the team can search the articles and link one, which shows on the ticket, and an article shows the tickets linked to it.
5. **Customer satisfaction.** When a ticket is solved, the customer can rate the answer from 1 to 5 and leave a comment, on a satisfaction page of its own that the customer would open from a link. No email is sent in this version: the solved ticket shows the link, so the team can open it to try it. The rating and comment show on the ticket and in the ticket list.
6. **A dashboard.** How support is going at a glance: ticket volume by week, the median time to first reply and to solve by priority, SLA breaches, and the satisfaction score over time, as charts. It should be visually striking, with at least a line chart and a bar chart.

### Sample data

Support comes with realistic sample data, so every screen looks alive the first time it starts: about 150 tickets from the past three months raised by the customers below, at every status and priority, with conversations, notes, status changes, some tickets close to a target and some breached, about 15 knowledge base articles linked to some of the tickets, and ratings on most of the solved tickets. The dates are relative to today, so a fresh copy always looks current.

The customers are the organizations and main contacts from Accountable's sample data (Accountable's other contacts can be invented to match):

| Organization | Industry | Main contact | Job title |
|---|---|---|---|
| Harbor & Pine | Hospitality | Sam Carter | Owner |
| Lantern Hotels | Hospitality | Elena Petrova | Head of Operations |
| Cobalt Ridge Roofing | Construction | Owen Walsh | Managing Director |
| Northlight Dental | Healthcare | Priya Nair | Practice Manager |
| Quarry Lane Brewing | Food and drink | Ben Adler | Co-founder |
| Kestrel Freight | Logistics | Jonas Weber | Operations Director |
| Fernhill Veterinary | Healthcare | Marcus Bell | Practice Owner |
| Bluebird Bakery | Food and drink | Ines Moreau | Founder |
| Saltmarsh Studio | Professional services | Noah Kim | Creative Director |
| Oakhaven Care | Healthcare | Grace Lindqvist | Finance Director |
| Stonebridge Accounting | Professional services | Aisha Rahman | Partner |
| Tallgrass Foods | Food and drink | Tomás Reyes | Supply Chain Manager |
| Greyfriars Property | Real estate | Daniel Osei | Portfolio Manager |
| Juniper Health | Healthcare | Hannah Okafor | Chief Operating Officer |
| Brightwater Solar | Energy | Ana Costa | General Manager |
| Marlowe Insurance | Financial services | Li Wei | IT Director |
| Pennant Sports Club | Education and leisure | Leo Marsh | Club Manager |
| Willow Creek Schools | Education and leisure | Fatima Haddad | Business Manager |
| Ironwood Joinery | Manufacturing | Ruth Adeyemi | Owner |
| Foxglove Interiors | Retail | Maya Lund | Showroom Manager |
| Copperline Electric | Construction | Carlos Vega | Operations Manager |
| Summit Trail Outfitters | Retail | Nora Hale | Head of Ecommerce |
| Alder & Finch Legal | Professional services | Yuki Tanaka | Office Manager |
| Redwood Print | Manufacturing | Peter Novak | Plant Manager |

All names are made up, and email addresses use the reserved `.example` domain.

## Affected users and systems

- The support team of four, using Support on one computer while they try it out.
- No other systems are involved yet. Support has its own database and doesn't read Accountable's.

## Constraints

- The technology in `docs/TECH_STACK.md`.
- It runs locally with `npm run dev`, which works on Mac, Linux and Windows. Node and uv must already be installed, and `README.md` says how.
- Every change is kept: it's still there after a browser refresh and after a restart.
- `npm run seed` resets the data to the sample data, after asking.
- Not in this version: sign-in or permissions, email or phone integration, a portal for customers beyond the satisfaction page, attachments, business hours or holidays in the SLA clocks, AI features, dark mode or a layout for phones.

## Success criteria

1. Someone non-technical can start Support with `npm run dev`, open it in a browser and land on the ticket list, with sample data on every screen.
2. Tickets can be added, found by searching and filtering, sorted, opened, answered and solved, and every change is still there after a refresh and after a restart.
3. Each ticket's time left against its targets is right for its priority, and breached tickets stand out.
4. Articles can be written, found and linked to tickets.
5. A solved ticket's satisfaction page takes a rating and a comment, which then show on the ticket.
6. The dashboard's charts match the tickets in the database.
