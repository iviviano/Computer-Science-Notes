

$$\begin{align}
&\text{Let }S \text{ be an empty list}\\
&indices=(0,0) \\
&\textbf{While } S_{0}[indices_{0}:]≠\emptyset\lor S_{1}[indices_{1}:]≠\emptyset \textbf{ do:} \\
&\quad \text{Pick }cur \text{ such that } S_{cur}[indices_{cur}]_{x}=\min\{S_{0}[indices_{0}]_{x},S_{1}[indices_{1}]_{x} \}  \\
&\quad oth = !cur\\
&\quad \textbf{If } indices_{oth}>0 \textbf{ then:}\\
&\quad \quad y=\max\{S_{cur}[indices_{cur}]_{y},S_{oth}[indices_{oth}-1]_{y}\} \\
&\quad \textbf{Else:} \\
&\quad \quad y = S_{cur}[indices_{cur}]_y\\
&\quad \textbf{end if} \\
&\quad x=S_{cur}[indices_{cur}]_{x} \\
&\quad \textbf{If } S==\emptyset\lor y≠last(S)_{y} \textbf{ then:} \\
&\quad \quad \text{Append } (x,y) \text{ to } S \\
&\quad \textbf{end if}\\
&\quad \text{Increment }indices_{cur}\text{ by }1\\
&\textbf{end while} \\
\end{align}$$

