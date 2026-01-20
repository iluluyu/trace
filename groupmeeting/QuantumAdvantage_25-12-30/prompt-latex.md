# Role & Context
You are a senior Postdoc in Quantum Information at Fudan University. You are an expert in LaTeX Beamer design, specifically using custom templates.
**Task:** Create the a LaTeX frmae 
**Audience:** Mixed background (Physics/CS). Some experts, some beginners.

# The Theme: "WritingLab - Quantum Spectrum"
I am using a custom theme file `beamerthemeWritingLab.sty`. You MUST strictly follow the component usage rules below to ensure the code compiles and looks professional.

## 1. Component Mapping Rules (CRITICAL)
Use the specific environments defined in my .sty file instead of generic blocks:

* **Core Concepts / Key Idea:** Use `\begin{stylebox}[1]{Title} ... \end{stylebox}` (Teal Color).
* **Math / Theorems:** * For standalone important equations: `\begin{eqbox}[3] ... \end{eqbox}` (Blue Pale Box).
    * For heavy emphasis equations: `\begin{bfeqbox}[3] ... \end{bfeqbox}` (Bold Filled Box).
    * For Theorems/Lemmas: Use the native `\begin{theorem}...\end{theorem}` or `\begin{lemma}...\end{lemma}` environments (The theme handles styling automatically).
* **Algorithms / Protocols:** Use `\begin{algorithm}[Name] ... \end{algorithm}` (Green Color).
* **Problems / Warnings:** Use `\begin{stylebox}[5]{Title} ... \end{stylebox}` (Orange Color).
* **Derivation / Proof Steps:** Use `\begin{proof} ... \end{proof}`.

## 2. Layout Constraints (Strict Compliance)
* **Use Columns for Split Views:** ```latex
    \begin{columns}
        \begin{column}{0.48\textwidth}
             % Left Content
        \end{column}
        \begin{column}{0.48\textwidth}
             % Right Content
        \end{column}
    \end{columns}
    ```
* **Visual Hierarchy:** * Never put more than **50 words** on a slide.
    * Use `\vspace{0.3cm}` between boxes.
    * Use `itemize` lists extensively.



# Input Content (The Paper)
[... Paste the abstract, intro, and key math sections of the paper here ...]


# Content Strategy (The Narrative)
Structure the presentation as follows:

1.  **Title Page:** `\maketitle` (The theme handles the gradient).
2.  **Motivation (The "Hook"):** * Use a `stylebox[1]` to define the problem intuitively (e.g., Hidden Switch / Parity).
    * Use a `stylebox[5]` to show why Classical methods fail (Complexity $O(n)$).
3.  **The Quantum Advantage:** * Visual comparison. Use `\begin{columns}`.
    * Left: Classical (Hard). Right: Quantum (Easy, $O(\sqrt{n})$).
4.  **Mechanism (The Math):**
    * **Do not** dump a wall of equations.
    * Show the Hamiltonian/Oracle using `\begin{bfeqbox}[3]`.
    * Explain the symmetry breaking using bullet points inside a `stylebox[6]` (Gray/Auxiliary).
5.  **Example (M4 State):**
    * Walk through the 4-qubit example.
    * If there is a circuit or state diagram needed, write: `\begin{center} [Placeholder for TikZ: 4-qubit state graph] \end{center}`.
6.  **Conclusion:** Recap using a `fillbox[BG_Teal]` for the take-home message.

Write the TikZ code for this specific diagram, using tikz-network or standard tikz nodes, strictly matching the colors WLTeal and WLOrange defined in my theme.