# Efficient iterated greedy for the two-dimensional bandwidth minimization problem <a href="https://doi.org/10.1016/j.ejor.2022.09.004"><img src="https://upload.wikimedia.org/wikipedia/commons/1/11/DOI_logo.svg" alt="DOI" width="20"/></a>

<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200&icon_names=mail" />

[![Elsevier Badge](https://img.shields.io/badge/Elsevier-FF6C00?logo=elsevier&logoColor=fff&style=flat)](https://doi.org/10.1016/j.ejor.2022.09.004)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Code](https://img.shields.io/badge/Code-Java_16-orange.svg)]()
[![Framework](https://img.shields.io/badge/Powered_by-MORK-green.svg)](https://mork-optimization.com/)
[![DOI](https://zenodo.org/badge/1126765424.svg)](https://doi.org/10.5281/zenodo.18132830)



## Abstract

Graph layout problems are a family of combinatorial optimization problems that consist of finding an embedding of the vertices of an input graph into a host graph such that an objective function is optimized. Within this family of problems falls the so-called Two-Dimensional Bandwidth Minimization Problem (2DBMP). The 2DBMP aims to minimize the maximum distance between each pair of adjacent vertices of the input graph when it is embedded into a grid host graph.

In this paper, we present an efficient heuristic algorithm based on the Iterated Greedy (IG) framework hybridized with a new local search strategy to tackle the 2DBMP. Particularly, we propose different designs for the main IG procedures (i.e., construction, destruction, and reconstruction) based on the trade-off between intensification and diversification. Additionally, the improvement method incorporates three advanced strategies: an efficient way to evaluate the objective function of neighbor solutions, a tiebreak criterion to deal with "flat landscapes", and a neighborhood reduction technique. Extensive experimentation was carried out to assess the IG performance over state-of-the-art methods, emerging our approach as the most competitive algorithm. Specifically, IG finds the best solutions for all instances considered in considerably less execution time.

## Authors


- Sergio Cavero <sup>1</sup> <a href="mailto:sergio.cavero@urjc.es" aria-label="Sergio Cavero Email"><img src="https://upload.wikimedia.org/wikipedia/commons/b/b1/Email_Shiny_Icon.svg" alt="email" width="20" style="vertical-align:middle;"/></a> <a href="https://orcid.org/0000-0002-5258-5915"><img src="https://upload.wikimedia.org/wikipedia/commons/0/06/ORCID_iD.svg" alt="ORCID" width="20" style="vertical-align:middle;"/></a>
- Eduardo G. Pardo <sup>1,*</sup> <a href="mailto:eduardo.pardo@urjc.es" aria-label="Eduardo G. Pardo Email"><img src="https://upload.wikimedia.org/wikipedia/commons/b/b1/Email_Shiny_Icon.svg" alt="email" width="20" style="vertical-align:middle;"/></a> <a href="https://orcid.org/0000-0002-6247-5269"><img src="https://upload.wikimedia.org/wikipedia/commons/0/06/ORCID_iD.svg" alt="ORCID" width="20" style="vertical-align:middle;"/></a>
- Abraham Duarte <sup>1</sup> <a href="mailto:abraham.duarte@urjc.es" aria-label="Abraham Duarte Email"><img src="https://upload.wikimedia.org/wikipedia/commons/b/b1/Email_Shiny_Icon.svg" alt="email" width="20" style="vertical-align:middle;"/></a> <a href="https://orcid.org/0000-0002-4532-3124"><img src="https://upload.wikimedia.org/wikipedia/commons/0/06/ORCID_iD.svg" alt="ORCID" width="20" style="vertical-align:middle;"/></a>


### Affiliations

1. Departamento de Informática y Estadística, Universidad Rey Juan Carlos — C. Tulipán, s/n, Móstoles, 28933, Madrid, Spain

<sup>*</sup>Corresponding author.

---


## Table of Contents

- [Repository Structure](#repository-structure)
- [Abstract](#abstract)
- [Authors](#authors)
- [Datasets](#datasets)
- [Code Execution](#code-execution)
- [Requirements](#requirements)
- [Results](#results)
- [License](#license)
- [Funding](#funding)
- [Citation](#citation)
- [Acknowledgments](#acknowledgments)
- [Powered by MORK](#powered-by-mork-metaheuristic-framewoRK)

---

## Repository Structure


```
.
├── code/                # Source code
├── instances/           # Problem instances
│   ├── harwell-boeing/  # Harwell-Boeing dataset
│   ├── prelim/          # Preliminary dataset
│   └── regular/         # Regular graphs dataset
|
├── paper/               # Paper and related materials
│   └── results/         # Paper results (deatiled result per instance)
|   
├── results/             # Experimental result, generated after code execution
├── LICENSE              # License file
└── README.md            # Project documentation (this file)
```

---



## Datasets

The computational tests are performed over 90 instances previously reported in the literature. All instances have been made publicly available at [https://www.heuristicas.es/](https://www.heuristicas.es/).

### Instance Format

The instances represent graphs $G=(V_G, E_G)$ to be embedded into a grid host graph.

### Dataset Statistics
| Dataset           | Instances | Vertices $\lvert V_G \rvert$ | Edges $\lvert E_G \rvert$ | Description                                               |
|-------------------|-----------|------------------------------|---------------------------|-----------------------------------------------------------|
| **Small Graphs**  | 45        | 5 – 21                       | 6 – 190                   | Topologically diverse small graphs.                       |
| **Harwell-Boeing**| 45        | 48 – 960                     | 78 – 7442                 | Representative sparse matrices from the Harwell-Boeing collection. |

## Code Execution (Java project using MORK)

### Running Experiments

Execution of the program can be done via the command line.

**Example 1:** Execute default experiment with the default set of instances
```bash
java -jar code/TDBMP.jar
```

**Example 2:** Execute using a different set of instances located inside the `[regular](instances/regular)` folder
```bash
java -jar code/TDBMP.jar --instances.path.default=instances/regular
```

**Example 3:** Execute using a different set of instances located inside the `newinstances` folder
```bash
java -jar code/TDBMP.jar --instances.path.default=newinstances
```

**Example 4:** Execute with custom parameters
```bash
java -jar code/TDBMP.jar --instances.path.default=newinstances --algorithm.maxIterations=1000 --seed=42
```

### Configuration Options

Available command-line parameters:
- `--instances.path.default`: Path to instances folder (default: `./instances/prelim`)
- `--seed`: Random seed for reproducibility (default: `1234`)
- `--output.path`: Output directory for results (default: `results`)

## Requirements

- Java 11 or higher
- Maven 3.6+ (for building from source)
- Minimum 4GB RAM recommended for large instances

### Dependencies

All dependencies are managed through Maven and will be automatically downloaded during the build process. Main dependencies include:
- MORK Framework (latest version)
- Apache Commons Math3
- JUnit 5 (for testing)

## Results

Experimental results are stored in the `results` folder after execution. Each result file includes:
- Instance name
- Best solution found
- Solution quality metrics
- Execution time
- Algorithm parameters used

Results can be analyzed using the provided visualization scripts in the `analysis` folder.



## License

This project is licensed under the **Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International (CC BY-NC-ND 4.0)** License.

### License Summary

**You are free to:**
- **Share** — copy and redistribute the material in any medium or format

**Under the following terms:**
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.
- **NonCommercial** — You may not use the material for commercial purposes.
- **NoDerivatives** — If you remix, transform, or build upon the material, you may not distribute the modified material.

**No additional restrictions** — You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.

### Notices

You do not have to comply with the license for elements of the material in the public domain or where your use is permitted by an applicable exception or limitation.

No warranties are given. The license may not give you all of the permissions necessary for your intended use. For example, other rights such as publicity, privacy, or moral rights may limit how you use the material.

For the full license text, see: [https://creativecommons.org/licenses/by-nc-nd/4.0/](https://creativecommons.org/licenses/by-nc-nd/4.0/)

**Alternative licenses:** If you require a different license for commercial or academic use, please contact the corresponding author.

## Funding

This research has been partially supported by:

- **Ministerio de Ciencia, Innovación y Universidades** (Grants Ref. PGC2018-095322-B-C22, PID2021-1257090A-C22, and FPU19/04098)
- **Comunidad de Madrid** and **European Regional Development Fund** (Grant Ref. P2018/TCS-4566)

---

## Citation

If you use this work in your research, please cite our paper:

<details>
<summary><strong>BibTeX</strong></summary>

```bibtex
@article{Cavero2023,
  title={Efficient iterated greedy for the two-dimensional bandwidth minimization problem},
  author={Cavero, Sergio and Pardo, Eduardo G. and Duarte, Abraham},
  journal={European Journal of Operational Research},
  volume={306},
  number={3},
  pages={1126--1139},
  year={2023},
  publisher={Elsevier},
  doi={10.1016/j.ejor.2022.09.004}
}
```
</details>

**APA Format:**

Cavero, S., Pardo, E. G., & Duarte, A. (2023). Efficient iterated greedy for the two-dimensional bandwidth minimization problem. *European Journal of Operational Research, 306*(3), 1126–1139. https://doi.org/10.1016/j.ejor.2022.09.004

---

## Acknowledgments

We would like to thank M.A. Rodríguez et al., authors of the previous most competitive method in the state of the art (BVNS), for sharing their code with us.

## Powered by MORK (Metaheuristic Optimization framewoRK)

| ![Mork logo](https://user-images.githubusercontent.com/55482385/233611563-4f5c91f2-af36-4437-a4b5-572b6655487a.svg) | MORK is a Java framework for easily solving hard optimization problems. You can [create a project](https://generator.mork-optimization.com/) and try the framework in under one minute. See the [documentation](https://docs.mork-optimization.com/en/latest/) or the [source code](https://github.com/mork-optimization/mork). |
|:--:|--|

---
