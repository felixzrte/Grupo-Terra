---
type: ship
faction: Inquisition
tags: 
aliases: 
parent: 
children:
  - "[[Underhive]]"
  - "[[Upper]]"
  - "[[Test]]"
---
```dataviewjs
const children = dv.current().children; // Access the `children` metadata field

if (children) {
  dv.table(
    ["File", "Type", "Faction", "Tags"], // Table headers
    children.map(link => {
      const page = dv.page(link); // Fetch child note's metadata
      return [
        page?.file.link || "N/A", // Link to the file
        page?.type || "N/A", // Get `type` or default to "N/A"
        page?.faction || "N/A", // Get `faction` or default
        page?.tags ? page.tags.join(", ") : "N/A" // Join tags array
      ];
    })
  );
} else {
  dv.paragraph("No children found in the metadata.");
}
```

