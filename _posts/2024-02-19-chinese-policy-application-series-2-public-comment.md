---
layout: post
title: "Chinese Policy Application Series #2 | Public Comment"
date: 2024-02-19
tags: [AI Ethics, Art, Travel]
---

## Disclaimer:

The content presented in this series is intended solely for educational and illustrative purposes within the context of a public policy course. This work represents my personal journey in learning about artificial intelligence and its applications in China, and should not be construed as professional advice, authoritative analysis, or an exhaustive examination of the subject matter.

All information and viewpoints expressed are based on publicly available sources and reflect my understanding at the time of writing. While efforts have been made to ensure accuracy and reliability, I do not claim completeness or absolute correctness, and readers are encouraged to conduct their own research and consult official sources for more detailed information.

This series does not intend to promote any political agenda or influence policy decisions, nor does it represent the views or positions of any institution or organization with which I may be affiliated. Any resemblance to real policies, events, or situations is coincidental and used purely for educational discussion.

I respect all cultural, national, and intellectual property rights, and no infringement or disrespect is intended through this work. Feedback and constructive dialogue are welcome to enhance understanding and promote thoughtful discussion on the topics explored.


Recipient: Office of the Central Cyberspace Affairs Commission

Author: 艾佳奕

Subject: Public Comment on the Draft Regulations on the Management of Generative Artificial Intelligence Services

Date: February 19th, 2024




To Whom It May Concern,




On behalf of the Institute of Artificial Intelligence Ethical Cooperation (IAIEC)[1], a non-profit organization dedicated to promoting regulated, ethical AI development and digital rights, we acknowledge and commend the efforts of the Cyberspace Administration of China in drafting regulations for generative artificial intelligence services in PRC. This letter presents our observations, concerns, and suggestions regarding specific sections of the draft, enhanced by relevant empirical findings on the application of artificial intelligence.




Enhanced Concerns and Recommendations:

Non-Discrimination in AI-generated Content (Article 4):
Observation: Article 4 mandates measures against discrimination, however, we note some insufficient specificity in the enforcement mechanisms and benchmarks for measuring bias.
Empirical Insight: A study examining AI-assisted criminal sentencing revealed systematic ethnic bias, where defendants of ethnic minority status received sentences up to 6.2% longer than Han defendants for identical crimes (Yang 2023). This indicates biases in AI algorithms that could replicate or exacerbate societal prejudices.
Recommendation: The IAIEC suggests implementing more laborious and transparent auditing mechanisms for AI algorithms, including mandatory bias impact assessments before deployment. These assessments should be publicly disclosed to the extent of incorporating various think tanks made of AI experts such as the China Academy For Information and Communication Technology (CAICT) and the Ministry of Industry and Information Technology (MIIT) to ensure accountability.
Data Legality and Diversity for Training (Article 7):
Observation: The requirement for data legality and diversity is crucial, however the draft does not specify methods for verifying data source integrity or diversity.
Empirical Insight: The same study from Eddie Yang demonstrates that AI can inherit and potentially amplify biases present in the training data, which accents the importance of diverse and unbiased datasets (Yang 2023). Since AI is trained on its input to produce a certain output, the input is fundamental to a more just output.
Recommendation: We advise to mandate the inclusion of diverse datasets in the AI training processes that ensures representation across different ethnic groups. Additionally, we encourage the CAC to introduce requirements for periodic bias audits of the datasets used, with findings to be made public. We acknowledge and are prideful of the many different ethnic groups within China and want to encourage the CAC to take this into account when making rules for more specific regions in terms of using more local data to better fit the circumstances of the level the rule operates within.
Prohibition of Discriminatory Content Generation (Article 12):
Observation: This article prohibits generating discriminatory content but does not address accountability and the remediation process for affected parties.
Recommendation: Establish a clear remediation and compensation mechanism for individuals or groups harmed by AI-generated discriminatory content. International examples include the EU’s approach to AI accountability in their AI Act, notifying the user that they are subject to the use of a high-risk AI system (European Union 2021, Art. 52).AI is a constantly developing technology, and it is wise to be prepared for the misjudgments of such an innovation. There need to be clear procedures for dealing with AI misconduct, which should notify the relevant developers and organizations, also providing users with a chance to provide feedback.




Conclusion:

We at the IAIEC support the proactive stance of the CAC towards creating more regulatory frameworks for the use of generative AI technologies. Incorporating detailed empirical evidence, accountability measures, more explicit language, and our recommendations into the regulatory process can help mitigate biases and ensure AI technologies serve the public good, fostering trust and inclusivity. We are committed to contributing further to this dialogue and offer our expertise in future discussions. Thank you for the chance to comment.




Sincerely,

艾佳奕
Policy Analyst, Institute of Artificial Intelligence Ethical Cooperation (IAIEC)
aa@iaiec.mail


[1] Made-up non-profit for this sample public comment. Any similarity to a real non-profit is purely coincidental and not intentional.

## References




European Union, "Proposal for a Regulation of the European Parliament and of the Council         Laying Down Harmonised Rules on Artificial Intelligence (Artificial Intelligence Act)        and Amending Certain Union Legislative Acts," accessed February 19, 2024,             https://artificialintelligenceact.eu/the-act/.




Yang, Eddie. Automated Repression: Ethnic Discrimination in AI-Assisted Criminal Sentencing   in China. working paper, 2023.

---

{% if page.tags %}
<div class="tag-row">
  {% for tag in page.tags %}
    <a class="tag-chip" href="{{ '/topics/' | relative_url }}#{{ tag | slugify }}">#{{ tag }}</a>
  {% endfor %}
</div>
{% endif %}
