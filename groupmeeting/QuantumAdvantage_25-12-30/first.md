%----------------------------------------------------------------------------------------
%   SLIDE 1: MOTIVATION
%----------------------------------------------------------------------------------------
\begin{frame}{The Permutation Parity Problem}
    \begin{stylebox}[1]{The Task}
        Consider $n$ particles. An agent applies a hidden permutation $\sigma \in S_n$ to them.
        \begin{itemize}
            \item We must determine if $\sigma$ is \textbf{Even} or \textbf{Odd}[cite: 5, 23].
            \item No oracles, no function evaluation, just a physical rearrangement[cite: 11, 23].
        \end{itemize}
    \end{stylebox}

    \vspace{0.5cm}

    \begin{stylebox}[5]{The Classical Limit}
        \begin{columns}
            \begin{column}{0.15\textwidth}
                \centering
                \Huge $\times$
            \end{column}
            \begin{column}{0.80\textwidth}
                Classically, to distinguish parity with certainty ($P_s=1$):
                \begin{itemize}
                    \item We need $n$ distinct labels (e.g., $n$ colors)[cite: 6].
                    \item With $< n$ labels, success is limited to random guessing ($P_s=1/2$)[cite: 27].
                \end{itemize}
            \end{column}
        \end{columns}
    \end{stylebox}
\end{frame}

%----------------------------------------------------------------------------------------
%   SLIDE 2: THE QUANTUM ADVANTAGE
%----------------------------------------------------------------------------------------
\begin{frame}{Theorem I: A Sharp Quantum Advantage}
    \begin{columns}
        \begin{column}{0.48\textwidth}
            \begin{stylebox}[6]{Classical Constraint}
                Linear scaling required:
                $$ d_{class} = n $$
                \vspace{0.2cm}
                If we lose just one label, perfect identification is impossible[cite: 26, 27].
            \end{stylebox}
        \end{column}

        \begin{column}{0.48\textwidth}
            \begin{stylebox}[1]{Quantum Threshold}
                Using entanglement, we can beat the classical limit significantly[cite: 7].
            \end{stylebox}
        \end{column}
    \end{columns}

    \vspace{0.5cm}

    % Heavy emphasis on the main result
    \begin{bfeqbox}[3]{Theorem I [cite: 30]}
        Perfect parity identification ($P_s=1$) is achievable iff the local dimension $d$ satisfies:
        $$ d \ge d_{min} := \lceil \sqrt{n} \rceil $$
    \end{bfeqbox}

    \begin{itemize}
        \item Example: For $n=4$ particles, Classical needs $d=4$. Quantum needs only $d=2$ (qubits)[cite: 34].
    \end{itemize}
\end{frame}

%----------------------------------------------------------------------------------------
%   SLIDE 3: MECHANISM (Schur-Weyl Duality)
%----------------------------------------------------------------------------------------
\begin{frame}{Mechanism: Symmetry Breaking}
    How does it work? We exploit the structure of the Hilbert space under the Symmetric Group $S_n$.

    \begin{stylebox}[1]{Schur-Weyl Decomposition [cite: 53]}
        $$ (\mathbb{C}^d)^{\otimes n} \cong \bigoplus_{\lambda} \mathcal{K}_{\lambda} \otimes \mathcal{H}_{\lambda} $$
        \begin{itemize}
            \item $\mathcal{K}_{\lambda}$: Irreps of $S_n$ (Permutations).
            \item $\mathcal{H}_{\lambda}$: Irreps of $SU(d)$ (Unitaries).
        \end{itemize}
    \end{stylebox}

    \vspace{0.3cm}
    
    \begin{theorem}[Parity Detection Condition]
        If $d \ge \lceil\sqrt{n}\rceil$, there exists a state $|\psi_e\rangle$ such that the subspaces spanned by Even ($A_n$) and Odd ($S_n \setminus A_n$) permutations are orthogonal[cite: 35]:
        $$ \sigma_{odd} |\psi_e\rangle \perp \sigma_{even} |\psi_e\rangle $$
    \end{theorem}
\end{frame}

%----------------------------------------------------------------------------------------
%   SLIDE 4: CONCRETE EXAMPLE (4 Qubits)
%----------------------------------------------------------------------------------------
\begin{frame}{Example: 4 Qubits ($n=4, d=2$)}
    Classically impossible ($d < 4$). Quantumly possible ($d = \sqrt{4} = 2$).

    \begin{stylebox}[1]{The Strategy}
        We use the self-conjugate irrep associated with the Young Diagram $[2,2]$ (or partition $4 = 2+2$)[cite: 102].
    \end{stylebox}

    \vspace{0.3cm}

    \begin{eqbox}[3]{The M4 State (Unnormalized) [cite: 70, 71]}
        \begin{aligned}
        |\psi_e\rangle &= |0011\rangle + |1100\rangle \\
                       &+ \zeta_3 (|0101\rangle + |1010\rangle) \\
                       &+ \zeta_3^2 (|0110\rangle + |1001\rangle)
        \end{aligned}
    \end{eqbox}
    \vspace{0.2cm}
    \footnotesize{Here $\zeta_3 = e^{2\pi i / 3}$. This is a specific superposition of Dicke states[cite: 74].}

    \vspace{0.3cm}

    \begin{stylebox}[6]{Result}
        Even permutations keep $|\psi_e\rangle$ in a specific subspace. Any Odd permutation maps it to an orthogonal subspace, allowing perfect discrimination via projective measurement[cite: 66].
    \end{stylebox}
\end{frame}

%----------------------------------------------------------------------------------------
%   SLIDE 5: RESOURCE ANALYSIS
%----------------------------------------------------------------------------------------
\begin{frame}{Entanglement Requirements}
    Is this "cheap" quantumness? No. The entanglement required is nearly maximal.

    \begin{columns}
        \begin{column}{0.48\textwidth}
            \begin{algorithm}[Geometric Measure (GME)]
                $$ E(|\psi\rangle) = 1 - \max_{SEP} |\langle \phi | \psi \rangle|^2 $$
                Distance to the closest separable state[cite: 147].
            \end{algorithm}
        \end{column}

        \begin{column}{0.48\textwidth}
            \begin{table}
                \centering
                \begin{tabular}{c c c}
                    \hline
                    $n$ & Required $E_{\lambda a}$ & $E_{max}$ (Known) \\
                    \hline
                    3 & $5/9$ & $5/9$ \\
                    4 & $7/9$ & $7/9$ \\
                    5 & $17/20$ & $\approx 0.96$ \\
                    \hline
                \end{tabular}
                \caption{Comparison of required vs. maximal entanglement[cite: 160, 161].}
            \end{table}
        \end{column}
    \end{columns}

    \vspace{0.3cm}

    \begin{stylebox}[5]{Observation}
        For $n=3$ and $n=4$, the protocol requires \textbf{maximally} entangled states[cite: 159].
    \end{stylebox}
\end{frame}

%----------------------------------------------------------------------------------------
%   SLIDE 6: CONCLUSION
%----------------------------------------------------------------------------------------
\begin{frame}{Conclusion}
    \begin{fillbox}[BG_Teal]
        \centering
        \textbf{Take Home Message}
    \end{fillbox}

    \vspace{0.5cm}

    \begin{itemize}
        \item \textbf{Sharp Advantage:} Determining permutation parity is impossible classically with $d < n$, but possible quantumly with $d \ge \sqrt{n}$[cite: 31].
        \item \textbf{Rigorous:} The advantage holds for \emph{every} $n$, not just asymptotically[cite: 38].
        \item \textbf{Resource Heavy:} It requires high multipartite entanglement (close to maximal)[cite: 163].
        \item \textbf{No Oracle:} This is a natural physical task (swapping particles), not a contrived black-box function[cite: 22].
    \end{itemize}
\end{frame}

\end{document}