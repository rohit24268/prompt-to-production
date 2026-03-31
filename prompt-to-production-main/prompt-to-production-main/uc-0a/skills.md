# skills.md — UC-0A Skills Definition

skills:
  - name: classify_complaint
    description: Classifies a single complaint row into category, priority, reason, and review flag.
    input: A dictionary representing one complaint row (e.g., complaint_id, description).
    output: A dictionary with keys complaint_id, category, priority, reason, and flag.
    error_handling: Continues processing; if ambiguous, sets flag to 'NEEDS_REVIEW'. Outputs 'Other' for category if completely invalid or missing.

  - name: batch_classify
    description: Reads an input CSV of complaints, applies classify_complaint to each row, and writes the structured results to an output CSV.
    input: File paths to input_path (string) and output_path (string).
    output: Writes parsed results to the output_path CSV file and returns nothing.
    error_handling: Must flag nulls, gracefully handle missing data, not crash on bad rows, and produce an output file even if some individual row classifications fail.
