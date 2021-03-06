# Interpretation-semantic-textual-similarity

Ce projet est basé sur le cadre du concours SemEval de 2016. 

Pour deux phrases de texte, s1 et s2, le modèle calcule la similarité entre s1 et s2 et renvoie un score de similarité. Bien que ce score soit utile pour de nombreuses tâches, il ne permet pas de savoir quelles parties des phrases sont équivalentes en termes de sens (ou très proches en termes de sens) et lesquelles ne le sont pas. 

Nous nous sommes donc concentrés sur ce problème.  

Nous travaillons à partir d’un dataset de paires de phrases déjà ‘tokenisées’.  

📌 Voici notre approche : 
- Identifier des morceaux de phrases (‘chunks’) ayant chacun une unité de sens 
- Alignement de paires de chunks 
- Evaluation de la similarité entre 2 chunks  

Type d'alignement : 
- EQUI : les deux chunks sont sémantiquement équivalents dans le contexte. 
- OPPO : les significations des chunks sont en opposition l'une avec l'autre dans le contexte. 
- SPE1 et SPE2 : les deux chunks ont des significations similaires, mais le chunk de la phrase 1 est plus spécifique que le chunk de la phrase 2 ; et vice versa.
- SIMI : significations similaires, mais pas de EQUI, OPPO, SPE1, ou SPE2. 
- REL : sens apparenté, mais pas de SIMI, EQUI, OPPO, SPE1 ou SPE2. 
- NOALI : ce chunk n'a pas de chunk correspondant dans l'autre phrase.  

Evaluation du score : 
Les scores pour NOALI seront ignorés. EQUI devrait avoir un score de 5. Les autres éléments doivent avoir un score supérieur à 0 mais inférieur à 5.  

Après avoir mis en place quelques baselines pour la réalisation de cette tâche, nous focalisons sur l'implémentation de modèles correspondant à l'état de l'art tels que les Transformers.
