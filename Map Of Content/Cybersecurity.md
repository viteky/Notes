# Cybersecurity


```dataview
list from [[]] and !outgoing([[]])
```

## [[Offensive Security]]

## [[Defensive Security]]

## [[Networking]]

## Cryptography 
- [[Public keys]]
- [[Hashing]]
## General Concepts
- [[CIA Triad]]
## Fundamentals
- [[Search skills]]
- [[Careers in Cyber]]



```dataviewjs
const rootMOC = dv.current().file.name;

// Helper function to create collapsible sections recursively
function createMOCSection(mocName, visited = new Set()) {
    if (visited.has(mocName)) return null; // prevent cycles
    visited.add(mocName);

    const file = dv.page(mocName);
    if (!file) return null;

    // Get links safely
    const links = file.links ?? [];

    // Create collapsible section
    const section = document.createElement("details");
    const summary = document.createElement("summary");
    summary.textContent = mocName;
    section.appendChild(summary);

    const ul = document.createElement("ul");

    for (const link of links) {
        const linkName = link.path ?? link;

        const linkedFile = dv.page(linkName);

        if (linkedFile && linkedFile.file.name.includes("MOC")) {
            const nestedSection = createMOCSection(linkName, visited);
            if (nestedSection) {
                const li = document.createElement("li");
                li.appendChild(nestedSection);
                ul.appendChild(li);
            }
        } else {
            const li = document.createElement("li");
            li.innerHTML = `[[${linkName}]]`;
            ul.appendChild(li);
        }
    }

    section.appendChild(ul);
    return section;
}

// Append the MOC tree to Dataview container
const mocTree = createMOCSection(rootMOC);
if (mocTree) dv.container.appendChild(mocTree);
```



