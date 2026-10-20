# Burpsuite: Repeater

## Overview

Learn how to use Repeater to duplicate requests in Burp Suite.

## What I Learned

- Learn how to use Repeater to duplicate requests in Burp Suite.

## Exercises

### Exercise 1 — [What is Repeater]

**Q1.** Which sections gives us a more intuitive control over our requests?
**Answer:** Inspector

### Exercise 2 — [Message Analysis Toolbar]

**Q1.** Which option allows us to visualize the page as it would appear in a web browser?
**Answer:** Render  

### Exercise 3 — [Inspector]

**Q1.** Which section in Inspector is specific to POST requests?
**Answer:** Body Parameters

### Exercise 4 — [Practial Example]

**Q1.** What is the flag you receive?
**Answer:** THM{Yzg2MWI2ZDhlYzdlNGFiZTUzZTIzMzVi}

### Exercise 5 — [Challenge]

**Q1.** See if you can get the server to error out with a "500 Internal Server Error" code by changing the number at the end of the request to extreme inputs.
What is the flag you receive when you cause a 500 error in the endpoint?
**Answer:** THM{N2MzMzFhMTA1MmZiYjA2YWQ4M2ZmMzhl}

### Exercise 6 — [Mini-Challenge]

**Q1.** Exploit the union SQL injection vulnerability in the site.
What is the flag?
**Answer:** THM{ZGE3OTUyZGMyMzkwNjJmZjg3Mzk1NjJh}

## Key Takeaways

Solid understanding of effectively utilising Repeater to edit, manipulate, and resend requests.

## Notes

**Request List:** Located at the top left of the tab, it displays the list of Repeater requests. Multiple requests can be managed simultaneously, and each new request sent to Repeater will appear here.

**Request Controls:** Positioned directly beneath the request list, these controls allow us to send a request, cancel a hanging request, and navigate through the request history.

**Request and Response View:** Occupying the majority of the interface, this section displays the Request and Response views. We can edit the request in the Request view and then forward it, while the corresponding response will be shown in the Response view.

**Layout Options:** Located at the top-right of the Request/Response view, these options enable us to customize the layout of the Request and Response views. The default setting is a side-by-side (horizontal) layout, but we can also choose a vertical layout or combine them in separate tabs.

**Inspector:** Positioned on the right-hand side, the Inspector allows us to analyze and modify requests in a more intuitive manner than using the raw editor. We will explore this feature in a later task.
Inspector is a supplementary feature to the Request and Response views in the Repeater module. It is also used to obtain a visually organized breakdown of requests and responses, as well as for experimenting to see how changes made using the higher-level Inspector affect the equivalent raw versions.
Inspector can be utilized both in the Proxy and Repeater module. In both instances, it is situated on the far-right side of the window, presenting a list of components within the request and response

**Target:** Situated above the Inspector, the Target field specifies the IP address or domain to which the requests are sent. When requests are sent to Repeater from other Burp Suite components, this field is automatically populated.

