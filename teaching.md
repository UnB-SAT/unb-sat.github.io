---
title: Teaching (FLIA)
nav_order: 6
---

# Teaching · Fundamentos Lógicos da IA
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

*Fundamentos Lógicos da IA* (FLIA) is the group's elective course, a hands-on tour
through the logical machinery behind artificial intelligence. It begins with
propositional and first-order logic, works through CNF, Boolean satisfiability and
knowledge compilation, and ends in automated planning with PDDL.

What gives the course its character is the set of challenges. They are designed so
that students examine the same problem through several formal lenses: a single puzzle
can be written as logical constraints (CNF and SAT), as a pseudo-Boolean model, or as
a planning domain in PDDL. Learning to move between these viewpoints, and to
understand why one encoding solves in seconds what another cannot finish, is the point
of the course. Most challenges are competitive and submitted through the MOJ judge, so
students do not merely model a problem; they compare their solutions against the whole
class, and the strongest ones present how they did it.

A sample of the challenges posed across editions:

| Challenge | How students attacked it | Submitted to MOJ |
|---|---|---|
| Minesweeper (Campo Minado) | CNF modeling and SAT inference | yes |
| Light Up (Akari) | pseudo-Boolean and SAT modeling | yes |
| Lights Out, and a Lights Out RGB variant | pseudo-Boolean and SAT modeling | yes |
| Bomberda | automated planning in PDDL | yes |
| N-puzzle | state-space search and planning | |
| Pac-Man | planning as SAT | yes |
| *FCT Entregas* (deliveries), scored on three tracks: Agile, Satisficing, Optimal | automated planning | yes |
| Connect-4 tournament | minimax and adversarial search | |

Most competitive challenges are submitted and ranked on the MOJ judge, and each
edition also includes designing and presenting PDDL and HDDL planning domains. Across
editions, students have modeled classic puzzles and games as SAT or as planning,
among them Minesweeper, Light Up, Lights Out, Bomberda, Pipe Mania and Puzznic, and
have also built adversarial agents, such as the minimax players in the Connect-4
tournament. That same reflex, asking what happens when a game is phrased as a logic or
planning problem, is what later grew into several of the theses listed above.

Editions: 2025-1, 2024-2, 2024-1, 2023-2, 2023-1, 2022-2.
Latest syllabus, materials and challenges: <https://www.brunoribas.com.br/flia/2025-1/>

