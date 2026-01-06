
- 目的：把一篇论文的参考文献整理成 APA 格式，包含原文链接、PDF 链接、Google 学术链接等，方便读者查阅原文。

**Case I:** PDF 论文中的参考文献提供了 DOI 号或完整的原文链接。

  - S1：把论文的 PDF 原文或 PDF 文档的链接发给 AI 
  - S2：贴入下面的提示词，让 AI 帮你提取参考文献并整理成 APA 格式

**Case II:** 仅有网页版提供了 DOI 号 (Crossref) 或完整的原文链接。

  - S1：从网页版复制完整的参考文献；
  - S2: 打开一个新的 .md 文档，按快捷键 `Alt + Ctrl + V` 贴入；必要时，可以使用正则表达式去除无关的内容，仅保留 `Google Scholar`, `DOI` 相关的信息即可。 

## 提示词

你是一位资深的学术助理，擅长从论文中提取参考文献并整理成规范的 APA 格式。请按照以下要求完成任务：

1. **提取参考文献**：从我提供的论文 PDF 原文或 .md / .txt 文档中提取所有参考文献，确保不遗漏任何一条。
2. 按如下格式要求整理参考文献：

```raw
1. arXiv 的工作论文，按此格式输出：'Yap, L. (2024). Inference with Many Weak Instruments and Heterogeneity (Version 3). arXiv. [Link](https://doi.org/10.48550/arXiv.2408.11193) (rep), [PDF](https://arxiv.org/pdf/2408.11193.pdf), [Google](<https://scholar.google.com/scholar?q=Inference with Many Weak Instruments and Heterogeneity (Version 3)>).'
2. NBER 的工作论文，按此格式：'Goldsmith-Pinkham, P., Hull, P., & Kolesár, M. (2025). Leniency Designs: An Operator’s Manual. National Bureau of Economic Research. [Link](https://doi.org/10.3386/w34473), [PDF](https://www.nber.org/system/files/working_papers/w34473/w34473.pdf), [Google](<https://scholar.google.com/scholar?q=Leniency Designs: An Operator’s Manual>).'
3. 正式发表的论文按此格式：'Dobbie, W., Liberman, A., Paravisini, D., & Pathania, V. (2021). Measuring Bias in Consumer Lending. The Review of Economic Studies, 88(6), 2799–2832. [Link](https://doi.org/10.1093/restud/rdaa078) (rep), [PDF](http://sci-hub.ren/10.1093/restud/rdaa078), [Google](<https://scholar.google.com/scholar?q=Measuring Bias in Consumer Lending>).'
   - 其中，'[PDF]({URL}) 中的 {URL} 可以酌情查询后填入，尽量保证是可以访问的链接
4. 其它工作论文尽量按上述格式，酌情提供尽可能有用的信息
```

