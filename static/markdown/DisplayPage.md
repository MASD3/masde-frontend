# Outline
- Create Cards to display each and every project Kohta, Kazuya, and Owen work on
	- Each card should be fairly dynamic, and the programming of each card should be seamless using Svelt through the heavy use of dynamic components
- Have the cards be filterable by the creator, and display a creator blurb alongside them
	- Each card should link to a markdown-style page explaining the process of the project, as well as the appropriate links to repos, frameworks, toolkits, math, and algorithms used.
## Repository:
- [https://github.com/MASD3/masde-frontend/tree/main]
## Svelt Components
- We want the upkeep and continued development of this page to be as seamless as possible, and we can facilitate this using svlet's strong component framework. 
- By making each project and each project author its own component, we effectively break up the responsibility of the page.
## HTML Routing
- Since each project has more information then possible to be contained in just the card, each project will have a link to a markdown file detailing the project with more information.
- The Style of this markdown file can be adjusted, but it is currently universal to every project. This may be able to be changed by the future implementation of the Content Management System (CMS).

