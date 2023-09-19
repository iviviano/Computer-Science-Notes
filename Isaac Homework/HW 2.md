

$$\begin{align}
&\text{Let }S \text{ be an empty list}\\
&indeces=(0,0) \\
&\textbf{While } S_{0}[indices_{0}:]≠\emptyset\land S_{1}[indices_{1}:]≠\emptyset \textbf{ do:} \\
&\quad cur=\text{ index of list with smaller first }x \text{-coor}\\
&\quad oth = !cur\\
&\quad \textbf{If } indices_{oth}>0 \textbf{ then:}\\
&\quad \quad y=\max\{S_{cur}[indices_{cur}]_{y},S_{oth}[indices_{oth}-1]_{y}\} \\
&\quad \textbf{Else:} \\
&\quad \quad y = S_{cur}[indeces_{cur}]_y\\
&\quad \textbf{end if} \\
&\quad x=S_{cur}[indices_{cur}]_{x} \\
&\quad \textbf{If } S==\emptyset\lor y>last(S)_{y} \textbf{ then:} \\
&\quad \quad \text{Append } (x,y) \text{ to } S \\
&\quad \textbf{end if}\\
&\quad \text{Increment }indeces_{cur}\text{ by }1\\
&\textbf{end while} \\
&\text{Append } S_{0}[indices_{0}:],S_{1}[indices_{1}:] \text{ to } S\\
\end{align}$$
Problem with not adding every point needed