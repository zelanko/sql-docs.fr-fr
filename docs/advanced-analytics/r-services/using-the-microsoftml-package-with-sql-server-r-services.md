---
title: "Utilisation du package MicrosoftML avec SQL Server R Services | Microsoft Docs"
ms.custom: ""
ms.date: "01/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 1c377717-e281-431e-8171-3924dcce1cdd
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# Utilisation du package MicrosoftML avec SQL Server R Services
Le package **MicrosoftML** fourni avec Microsoft R Server et SQL Server vNext CTP 1.0 comprend plusieurs algorithmes Machine Learning développés par Microsoft qui prennent en charge le traitement multicœur et le streaming rapide des données. Ce package comprend également des transformations pour le traitement de texte et la caractérisation.

### <a name="new-machine-learning-algorithms"></a>Nouveaux algorithmes Machine Learning


-  **Linéaire rapide.** Apprentissage linéaire basé sur l’élévation stochastique à double coordonnée, qui peut être utilisé pour la régression ou la classification binaire. Le modèle prend en charge la régularisation L1 et L2.

- **Arborescence rapide.** Algorithme d’arbre de décision optimisé, connu sous le nom de FastRank et développé pour être utilisé dans Bing. Il s’agit de l’un des apprentissages les plus rapides et les plus populaires. Il prend en charge la régression et la classification binaire.

- **Forêt rapide.** Modèle de régression logistique basé sur la méthode de forêt aléatoire. Il est similaire à la fonction `rxLogit` dans RevoScaleR, mais il prend en charge la régularisation L1 et L2. Il prend en charge la régression et la classification binaire.

- **Régression logistique.** Modèle de régression logistique similaire à la fonction `rxLogit` dans RevoScaleR, avec prise en charge supplémentaire de la régularisation L1 et L2. Il prend en charge la classification multiclasse ou binaire.

- **Réseau neuronal.** Modèle de réseau neuronal pour la classification binaire, la classification multiclasse et la régression. Il prend en charge l’accélération GPU et les réseaux complexes personnalisables.

- **SVM à une classe.** Modèle de détection d’anomalie basé sur la méthode SVM, qui peut être utilisée pour la classification binaire dans les jeux de données non équilibrés.

## <a name="transformation-functions"></a>Fonctions de transformation

Le package **MicrosoftML** comprend également les fonctions suivantes qui peuvent être utilisées pour transformer des données et extraire des caractéristiques.

- `featurizeText()`
 
  Génère les nombres de ngrams dans une chaîne de texte donnée. 

  Cette fonction permet de détecter la langue utilisée, d’effectuer la normalisation et la segmentation du texte en unités lexicales, de supprimer les mots vides et de générer des caractéristiques à partir du texte. 

- `categorical()`

  Génère un dictionnaire de catégories et transforme chaque catégorie en vecteur d’indicateur. 
 
- `categoricalHash()`

  Convertit des valeurs catégoriques en tableau d’indicateurs en hachant la valeur et en utilisant le hachage comme index dans le conteneur.  

- `selectFeatures()` 

  Sélectionne un sous-ensemble de caractéristiques à partir de la variable donnée, soit en comptant les valeurs autres que les valeurs par défaut, soit en calculant un score d’information mutuelle concernant l’étiquette. 

Pour plus d’informations sur ces nouvelles fonctionnalités, consultez [MicrosoftML, fonctions](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml).

## <a name="support-for-microsoftml-in-r-services"></a>Prise en charge de MicrosoftML dans R Services

Le package **MicrosoftML** est entièrement intégré au pipeline de traitement des données utilisé par le package **RevoScaleR**. Actuellement, vous pouvez utiliser le package **MicrosoftML** dans n’importe quel contexte de calcul basé sur Windows, notamment SQL Server R Services.



## <a name="see-also"></a>Voir aussi


[Informations de référence sur les fonctions RevoScaleR](https://msdn.microsoft.com/microsoft-r/scaler/scaler)

