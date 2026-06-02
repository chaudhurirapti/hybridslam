A taxonomy and benchmark-oriented review of sensor-driven SLAM for autonomous navigation
and 
formation of Hybrid SLAM

Reliable autonomous navigation depends on the ability of mobile robotic platforms to estimate their
own motion while constructing consistent representations of unfamiliar, dynamic, or GPS-denied
environments. This review examines recent developments in simultaneous localisation and mapping
(SLAM) from the perspective of machine vision and sensor-driven perception for autonomous naviga-
tion. Drawing on 178 selected studies published between 2000 and 2026, it organises the field around
three interrelated dimensions: sensing modalities, localisation and mapping formulations, and algorith-
mic families for practical deployment. First, the review compares active positioning, proprioceptive,
and exteroceptive sensors, including GNSS, IMU, wheel odometry, LiDAR, radar, RGB-D, monocular,
stereo, and event-based cameras, and analyses their suitability for indoor, outdoor, structured, and
unstructured scenarios. Second, it synthesises core SLAM components, including landmark extraction,
data association, state estimation, map initialisation, and map updating, with attention to probabilis-
tic, graph-based, feature-based, direct, and learning-enhanced approaches. Third, it discusses metric,
topological, semantic, and hybrid map representations, relating them to application requirements such
as robustness, computational efficiency, scalability, and interpretability. To support systematic com-
parison, the review highlights commonly used evaluation criteria, including Absolute Trajectory Error,
Relative Pose Error, runtime, robustness under sensor noise, and domain-specific constraints. The
paper further identifies unresolved challenges in dynamic environments, cross-sensor calibration, long-
term map maintenance, benchmark consistency, real-time deployment on embedded platforms, and
the reproducibility of comparative results. By consolidating sensor trends, methodological taxonomies,
and application-oriented evaluation criteria, this review aims to provide a structured reference for
researchers and practitioners designing reliable SLAM systems for autonomous navigation.

<img width="704" height="594" alt="slam_overview(1)" src="https://github.com/user-attachments/assets/99af34e7-5784-4f38-81fc-f7d5ac6a4e88" />
<img width="6764" height="4125" alt="slam_overview" src="https://github.com/user-attachments/assets/9c56de7f-9963-4ed8-9046-3be7ad944183" />

A substantial number of SLAM-based studies have been published addressing various dimensions of SLAM research, the presented work distinctly differs in terms of its perspective, analytical depth, and evaluation framework. The major contributions of this review work are mentioned:

    1. This review presents a unified comparative taxonomy of sensor modalities — spanning active positioning, proprioceptive, and exteroceptive sensor classes. This has been complemented by a quantitative trend analysis of sensor technology adoption from 2000 to 2026, that provides major insight into the shifting hardware preferences in SLAM-based autonomous navigation research.
    2.  An analytical framework is presented evaluating four principal SLAM mapping paradigms — metrical, topological, semantic, and hybrid — through year-wise research frequency analysis. The paper additionally focuses on algorithm-level comparison, and domain-specific performance characterization, that enables evidence-based selection of optimal map representations for real-world autonomous navigation deployments.
    3. The survey synthesizes SLAM algorithm adoption patterns across different domains and systematically derives distinct open research challenges from the gaps identified within the reviewed literature. The process constitutes a structured technical road-map for the development of next-generation robust, scalable, and computationally efficient SLAM architectures.
    \section{Review methodology}
Review Methodology

Problem identification and formulation constitute the initial stage of the review methodology, followed by a structured exploration of domain-specific literature. This review focuses on SLAM-mediated point-to-point navigation, with particular emphasis on sensor-driven perception and decision-making. A systematic literature search was conducted across five bibliographic databases — Google Scholar, Science Direct, Scopus, Springer, and IEEE Xplore — covering publications from January 2000 to March 2026. Three hierarchical search strings were applied: S1. ("SLAM") OR ("simultaneous localization and mapping") AND ("autonomous navigation"); S2. "S1" AND ("sensor" OR "LiDAR" OR "camera" OR "IMU" OR "RGB-D"); and S3. "S2" AND ("mobile robot" OR "AGV" OR "autonomous vehicle" OR "path planning"). Searches were restricted to peer-reviewed, English-language articles with full text available. An initial retrieval of approximately 310 records was obtained across all databases, supplemented by near-about 25 additional records identified through snowballing and manual reference checking. Following automated and manual deduplication, approximately 250 unique records were retained for screening. After a two-stage screening process described below, 178 papers were identified as meeting the inclusion criteria and were retained for detailed evaluation. Of the 178 included papers, approximately 100 focus on the analysis of SLAM across localization and mapping domains, 45 examine application-specific SLAM formulations across domains such as autonomous driving, indoor navigation, underwater systems, and mining, and the remaining 33 address the development and benchmarked implementation of SLAM algorithms. <img width="1102" height="1306" alt="prisma_review" src="https://github.com/user-attachments/assets/422ba31f-900a-470a-98ac-3bac86eba1a3" />

The screening process was conducted in two sequential stages: 

   1.  In Stage 1, titles and abstracts of all approximately 250 records were independently screened against the inclusion criteria; approximately 45 records were excluded at this stage for being unrelated to SLAM, addressing domains outside the scope of this review (e.g., purely medical or satellite-based mapping), or lacking peer-review status. 
    2.  In Stage 2, the full texts of the remaining approximately 205 records were assessed for eligibility. Furthermore, 27 records were excluded at this stage for the following reasons: out of scope or domain mismatch), insufficient methodological detail or unreproducible results, and non-English language content identified post-retrieval. 
    

The survey of the papers were included if they: (i) addressed SLAM-mediated point-to-point navigation in mobile robotic or autonomous vehicle platforms; (ii) examined at least one of the following dimensions — sensor modalities, localization strategies, or map representation; (iii) were published between January 2000 and March 2026; and (iv) were peer-reviewed and available in English. Papers were excluded if they addressed SLAM solely in non-navigation contexts (e.g., surgical robotics, satellite remote sensing), if their experimental results were not reproducible or verifiable from the reported methodology, or if they were review articles without original comparative analysis. The selected 178 studies were then analyzed to evaluate sensor dependencies in SLAM frameworks, including a year-wise assessment of sensor utilization trends reported by different researchers for visual map generation and path planning applications. Subsequently, localization strategies and map representations are examined to identify their roles in enabling advanced and reliable navigation solutions. Key technical contributions are extracted from the selected articles to highlight advancements in autonomous navigation achieved through customized SLAM architectures.

Some important tables are mentioned below that will give a brief idea and clear evidence to select the combination of sensor-driven SLAM techniques in different environment types and deployment parameters. Localization, mapping strategies are also investigated and included here.<img width="615" height="464" alt="3" src="https://github.com/user-attachments/assets/3dff96fb-2081-4d26-a937-75f1abdb2793" />
<img width="626" height="664" alt="2" src="https://github.com/user-attachments/assets/dfda41f3-3ea5-448a-beab-5567dd830f4c" />
<img width="618" height="603" alt="4" src="https://github.com/user-attachments/assets/d62a2fe5-7a87-4849-908b-e69a25b6da87" />
<img width="638" height="613" alt="6" src="https://github.com/user-attachments/assets/9e272c47-81de-437b-9a0f-22f6694d1a1e" />
<img width="638" height="808" alt="5" src="https://github.com/user-attachments/assets/2473d3dd-a79b-4680-be15-4fd63e4b0034" />
<img width="624" height="735" alt="1" src="https://github.com/user-attachments/assets/7b28d336-88c9-4394-b3c7-2c90fd310393" />

Discussions:

This paper presented a structured analysis of Simultaneous Localization and Mapping (SLAM) for intelligent autonomous navigation. It covered sensor modalities, localization strategies, and
mapping paradigms. Development of a comparative framework that integrates qualitative taxonomy with quantitative benchmarking (ATE, RPE, and runtime) adds a key contribution, enabling objective evaluation of SLAM approaches across standard datasets. The study further provides a taxonomy-based classification of metric, topological, semantic, and hybrid SLAM, highlighting their respective strengths, limitations, and applicability. Advancements and research trends of the SLAM procedures are surveyed and included in this work, that provides an insightful side.
Through performance analysis, it is observed that LiDAR-based methods offer robustness in large-scale environments, while vision-based and semantic approaches provide flexibility and contextual
understanding in complex or dynamic scenarios. Additionally, this work contributes a practical perspective for method selection, linking SLAM performance to environmental conditions and system requirements, thereby supporting real-world deployment decisions. Despite these contributions, challenges remain in achieving scalability, robustness in dynamic environments, and computational
efficiency. Future work would focus on hybrid and learning-integrated SLAM frameworks with improved adaptability and standardized evaluation protocols. Beyond descriptive synthesis, this review offers five reusable contributions designed to support direct application by researchers. First, a unified taxonomy table consolidates sensor configurations, mapping paradigms, algorithmic families, benchmark datasets, evaluation metrics, hardware requirements, and deployment scenarios into a single cross-referenced reference, enabling
selection of a complete SLAM configuration from a single source. Second, an expanded benchmark matrix enables quantitative comparison of fifteen representative algorithms across standard datasets, augmented with computational feasibility and dynamic environment robustness annotations that are absent from individual algorithm papers. Third, an algorithm selection decision guide (Table 10) maps primary and secondary deployment constraints directly to recommended SLAM approaches with supporting rationale, providing a structured entry point for system designers. Fourth, a consolidated dataset and metrics reference summarises all benchmark datasets and evaluation metrics referenced across the review, including ground truth sources, applicable algorithms, and metric sensitivity characteristics, forming a self-contained evaluation planning resource. Fifth, a sensor selection guide provides environment-specific, range-
specific, and budget-aware hardware recommendations derived from the sensor performance analysis in Section 3. Together, these artifacts are intended to enable evidence-based SLAM system
design without requiring exhaustive re-reading of primary literature, and to serve as stable reference points for future comparative studies.


 
