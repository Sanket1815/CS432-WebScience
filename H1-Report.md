# Q1

### a) SCC

SCC: `{‘A’, ‘B’, ‘C’, ‘D’, ‘G’}` because as we can see from the graph A and B are bidirectional links, then B is connected towards C, C to D, and D to A ensures a cyclic path and C to G and G to C through G.

### b) IN

IN: `{‘M’}` because the IN component includes nodes that can reach the SCC but cannot be reached back. So here in the graph, M can reach the SCC but has no incoming connections from the SCC.

### c) OUT

OUT: `{‘H’, ‘L’}` because the OUT component includes nodes that can be reached from the SCC but cannot reach back. Here, as we can see in the graph, H and L are reachable from SCC but they do not have a path back to SCC.

### d) Tendrils

Tendrils are nodes that are reachable from IN but do not reach SCC and reach OUT but do not come from SCC. No tendrils are NOT reachable from IN and OUT.

### e) Tubes

Tubes are paths that connect IN and OUT without passing through SCC, and there are NONE such paths.

### f) Disconnected Nodes

Disconnected nodes are completely isolated from SCC, IN, and OUT. So let’s examine the following nodes:

- `{E} > {F, O}`
- `F > G` but `G` is in GCC
- `O > J > N`
- `N > L` but `L` is OUT, `N` is a disconnected component not part of SCC.
- `K > I` again isolated connection not reaching SCC.
- `J > N` here J and N are connected but do not reach SCC.

Thus, the disconnected components are `{E, F, O, J, N, K, I}`.

---

# Q2

### a)

![Q2 a)](/public/images/Q2-a.png)

### b)

```bash
curl -v -L -A "CS432/532" https://www.cs.odu.edu/~mweigle/courses/cs532/ua_echo.php
```

![Q2 b)](/public/images/Q2-b.png)

### c)

```bash
curl -L -A "CS432/532" -o output.html https://www.cs.odu.edu/~mweigle/courses/cs532/ua_echo.php
```

![Q2 c)](/public/images/Q2-c.png)

### d)

On Browser: `Output.html`
![Q2 d)](/public/images/Q2-d.png)

---

# Q3

The script starts with a seed URL and extracts all the links from the page using the BeautifulSoup library.

- Each extracted link is checked to ensure it is an HTML page by verifying the Content-Type header and has more than 1000 bytes of content using the Content-Length header.
- Valid links are stored in a set to ensure uniqueness, and the script continues crawling by treating these valid links as new seed URLs.
- To prevent overloading servers, a random delay is added between requests using time.sleep(random.uniform(1,3))
- The process repeats until at least 500 unique URIs are collected, ensuring that only useful web pages are included.
- The collected URIs are saved into a file named saved_links.txt, which can be used for further analysis or assignments.

### Google Colab:

[Google Colab Link](https://colab.research.google.com/drive/1d7kADvHHz39zHCGgEMKkMhHx1zNpsbjG?usp=sharing)

### Text File

[500 Output File](/public/files/saved_links.txt)
