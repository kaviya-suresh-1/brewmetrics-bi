# REFLECTION.md

## Reflection

Working on BrewMetrics helped me understand that a Power BI report is
not only about creating charts. The data model, DAX calculations, visual
design and version-control process all affect the final result.

The star-schema approach made the report easier to organise because
`Fact_Sales` contains transaction-level data while `Dim_Date`,
`Dim_City` and `Dim_Product` provide descriptive context. Separate DAX
measures also made the report reusable because the same `Total Sales`
measure can be used across different visuals and filters.

The assignment required Copilot-assisted DAX development. During the
final documentation stage, the Power BI Copilot interface could not
connect to a compatible workspace, so the Copilot documentation was
reconstructed from the required measures and completed model rather than
copied from a saved Copilot chat. This highlighted that AI assistance
depends on the environment and that generated logic still needs to be
checked against the actual model.

The DAX requirements covered different analytical patterns: growth using
time intelligence, cumulative totals, ranking with `RANKX`, and an
additional business metric. I learned that generated DAX should not
simply be accepted without checking filter context and business meaning.

Using GitHub also changed the workflow compared with a normal Power BI
lab. The project was maintained as a Power BI Project under version
control, making the development process easier to review.

Overall, the project improved my understanding of data modelling, DAX,
dashboard design and version-controlled BI development.
