---
# You can also start simply with 'default'
theme: slidev-theme-ustc
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://bu.dusays.com/2024/10/24/671921799465a.png
# some information about your slides (markdown enabled)
title: group2.28
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

# From Commands to Prompts:LLM-based Semantic File System

ICLR 2025

<!-- <div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
  Press Space for next page <carbon:arrow-right />
</div>

<div class="abs-br m-6 text-xl">
  <button @click="$slidev.nav.openInEditor" title="Open in Editor" class="slidev-icon-btn">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div> -->

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# Basic Introduction

本文介绍了一种基于LLM的语义文件系统（LLM-based Semantic File System），简称LSFS，该文件系统将命令行操作转换为自然语言提示，以提高用户的工作效率。属于大模型和系统结合的应用。


LSFS介于用户和文件系统之间，通过自然语言来操作文件系统，而不是通过命令行。
解决了两个问题：

* LSFS通过LLM模型来理解用户的自然语言提示，并将其转换为文件系统的操作，避免了记忆复杂的操作。

* LSFS利用向量数据库根据文件的语义信息，对文件系统进行总结，实现语义检索（Semantic File System）和一些复杂操作。


![](https://bu.dusays.com/2025/02/27/67c014fe2cfea.png){width=70%}

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/features/slide-scope-style
-->

<!-- <style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style> -->

<!--
Here is another comment.
-->

---
transition: slide-up
# level: 2
---

# Part I: Semantic File System

使用 all-MiniLM-L6-v2模型(proposed in 2019) 将文件系统转化为向量数据库。

利用向量数据库，可以实现一些在传统文件系统中难以实现的功能，如语义检索，语义聚合。

![](https://bu.dusays.com/2025/02/27/67c01a6743e9b.png){width=80%}

如图`Semantic_retrieve`，`group_semantic`，等操作。


---
trasintion: slide-up
---

# Part II: Command to Prompt

将命令行操作转化为自然语言提示。文中称为`LSFS Parser`。

这一部分多数是Prompt engineering的工作，通过设计合适的prompt，将自然语言转化为文件系统操作。

![](https://bu.dusays.com/2025/02/27/67c01eab8e6ff.png){width=60%}




---
trasition: fade-out
---

# Part III: Additional Design

* Rollback: 版本管理，回滚修改，避免不可逆操作。
* Human Verification：增删需要确认，避免模型错误操作。

![](https://bu.dusays.com/2025/02/27/67c01fdd27f74.png){width=80%}

---
transition: fade-out
---


# Example

如图是一个求`summary`的例子，
![](https://bu.dusays.com/2025/02/27/67c01d5c93ff8.png)

---
transition: fade-out
---

# Experiment Results
LSFS、LLM、Human三者做了消融实验。

主要`metric`有accuracy/precision/recall/F1，speedup 等等。
![](https://bu.dusays.com/2025/02/27/67c0232e3db69.png){width=80%}


---
transition: fade-out
---

非语义结果：
![](https://bu.dusays.com/2025/02/27/67c022ceed700.png){width=75%}

语义结果：
![](https://bu.dusays.com/2025/02/27/67c021f33ebf0.png){width=75%}


---
transition: fade-out
---

# Conclusion

* 提出了一种基于LLM的语义文件系统，将命令行操作转化为自然语言提示，提高用户的工作效率。
* 通过向量数据库实现了语义检索，语义聚合等功能。

<br>

# Weekness and Future Work 

* 创新性：没有太多创新性，主要是将LLM应用到文件系统中，聚合了一些不同模型来完成目标任务。
* 安全性问题：如何保证用户的文件安全？
* 性能问题：File system规模扩大后，如何提高模型的速度？
* 有错误率，这方面没什么特别好的办法（llm-based）。

<br>

# Thoughts

用过许多AI ide，ai集成开发环境，code generation/code completion/Terminal integration等等，确实能提升一部分效率。但准确率和效率还有很大的提升空间。这个方向也是目前llm落地商业化的比较常见的场景。

---
layout: center
class: text-center
---

# Thanks for your time!
