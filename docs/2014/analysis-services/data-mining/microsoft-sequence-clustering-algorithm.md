---
title: Algorithme Microsoft Sequence Clustering | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clusters [Analysis Services]
- algorithms [data mining]
- sequence clustering algorithms [Analysis Services]
- sequence [Analysis Services]
ms.assetid: ae779a1f-0adb-4857-afbd-a15543dff299
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3df71a2facc01abcb3ebdec57aaf243c0b7fda7d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66083833"
---
# <a name="microsoft-sequence-clustering-algorithm"></a>Algorithme MSC (Microsoft Sequence Clustering)
  Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithme Sequence Clustering est un algorithme d’analyse de séquence fourni par [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Vous pouvez utiliser cet algorithme pour Explorer les données qui contient les événements qui peuvent être liés en suivant des chemins ou *séquences*. L'algorithme recherche les séquences les plus communes en groupant, ou en regroupant en clusters, les séquences identiques. Voici quelques exemples de données qui contiennent des séquences qui peuvent être utilisées pour l'exploration de données, pour fournir des précisions sur des problèmes courants ou des scénarios d'entreprise :  
  
-   Séquence de clics qui sont créées lorsque les utilisateurs parcourent un site Web.  
  
-   Journaux qui répertorient les événements précédant un incident, tels que la défaillance d'un disque dur ou le blocage d'un serveur.  
  
-   Enregistrements de transaction qui décrivent l'ordre dans lequel un client ajoute des articles dans son panier d'achat sur un site de vente en ligne.  
  
-   Enregistrements qui suivent les interactions du client (ou du patient) au fil du temps, pour prévoir les annulations de service ou d'autres résultats de qualité médiocre.  
  
 Cet algorithme est semblable à de nombreux égards à l’algorithme de gestion de clusters [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Toutefois, au lieu de rechercher des clusters de cas qui contiennent des attributs similaires, l’algorithme MSC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering) recherche des clusters de cas qui contiennent des chemins similaires dans une séquence.  
  
## <a name="example"></a>Exemple  
 Le [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] site Web de collecte des informations sur les pages du site les utilisateurs visitent et sur l’ordre dans lequel les pages sont consultées. Comme la société permet de commander en ligne, les clients doivent se connecter au site. Cela fournit à la société des informations sur les clics effectués pour chaque profil de client. En utilisant l'algorithme MSC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering) sur ces données, la société peut détecter des groupes, ou des clusters, de clients qui présentent des modèles ou des séquences de clics similaires. La société peut ensuite utiliser ces clusters pour analyser comment les utilisateurs se déplacent sur le site Web, pour identifier les pages les plus étroitement liées à la vente d'un produit particulier et pour prévoir les pages qui ont le plus de chance d'être consultées ensuite.  
  
## <a name="how-the-algorithm-works"></a>Fonctionnement de l'algorithme  
 L’algorithme MSC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering) est un algorithme hybride qui associe les techniques de clustering à l’analyse en chaînes de Markov pour identifier les clusters et leur séquence. Une des particularités de l'algorithme MSC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering) est qu'il utilise des données de séquence. Ces données représentent généralement une série d'événements ou de transitions entre des états dans un dataset, comme par exemple une série d'achats de produits ou de clics Web pour un utilisateur particulier. L’algorithme examine toutes les probabilités de transitions et mesure les différences, ou distances, entre toutes les séquences possibles dans le dataset pour identifier les séquences les mieux adaptées pour servir d’entrées au clustering. Une fois que l'algorithme a créé la liste des séquences candidates, il utilise les informations de séquence comme entrée pour la méthode EM de clustering.  
  
 Pour obtenir une description détaillée de l’implémentation, consultez [Références techniques relatives à l’algorithme MSC (Microsoft Sequence Clustering)](microsoft-sequence-clustering-algorithm-technical-reference.md).  
  
## <a name="data-required-for-sequence-clustering-models"></a>Données requises pour les modèles Sequence Clustering  
 Lorsque vous préparez des données à utiliser pour l'apprentissage d'un modèle Sequence Clustering, vous devez comprendre les spécifications liées à l'algorithme, y compris la quantité de données requises et le mode d'utilisation des données.  
  
 Les spécifications d'un modèle Sequence Clustering sont les suivantes :  
  
-   **Une seule colonne clé** Un modèle Sequence Clustering requiert une clé qui identifie les enregistrements.  
  
-   **Une colonne de séquence** Pour les données de séquence, le modèle doit avoir une table imbriquée qui contient une colonne d’ID de séquence. L'ID de séquence peut être tout type de données pouvant être trié. Par exemple, vous pouvez utiliser un identificateur de page Web, un entier ou une chaîne de texte, tant que la colonne identifie les événements dans une séquence. Un seul identificateur de séquence est autorisé pour chaque séquence, et un seul type de séquence est autorisé dans chaque modèle.  
  
-   **Des attributs non-séquence facultatifs** L’algorithme prend en charge l’ajout d’autres attributs non liés à un séquencement. Ces attributs peuvent inclure des colonnes imbriquées.  
  
 Prenons l'exemple cité précédemment concernant le site Web [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] , un modèle Sequence Clustering peut inclure des informations sur les commandes sous forme de table de cas, des statistiques démographiques sur un client spécifique pour chaque commande sous forme d'attributs non-séquence et une table imbriquée contenant l'ordre dans lequel le client a parcouru le site ou a placé des articles dans son panier sous forme d'informations de séquence.  
  
 Pour des informations plus détaillées sur les types de contenu et les types de données pris en charge pour les modèles Sequence Clustering, consultez la section relative aux spécifications dans [Références techniques relatives à l’algorithme MSC (Microsoft Sequence Clustering)](microsoft-sequence-clustering-algorithm-technical-reference.md).  
  
## <a name="viewing-a-sequence-clustering-model"></a>Affichage d'un modèle Sequence Clustering  
 Le modèle d'exploration de données que crée cet algorithme contient les descriptions des séquences les plus courantes dans les données. Pour explorer le modèle, vous pouvez utiliser la **Visionneuse de l’algorithme MSC (Microsoft Sequence Cluster)**. Lorsque vous affichez un modèle Sequence Clustering, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vous montre des clusters qui contiennent plusieurs transitions. Vous pouvez également afficher des statistiques pertinentes. Pour plus d’informations, consultez [Explorer un modèle à l’aide de la visionneuse de l’algorithme MSC (Microsoft Sequence Cluster)](browse-a-model-using-the-microsoft-sequence-cluster-viewer.md).  
  
 Si vous voulez en savoir plus, vous pouvez parcourir le modèle dans la [Visionneuse de l’arborescence de contenu générique Microsoft](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md). Le contenu stocké pour le modèle inclut la distribution de toutes les valeurs dans chaque nœud, la probabilité de chaque cluster et des détails concernant les transitions. Pour plus d’informations, consultez [Contenu du modèle d’exploration de données pour les modèles Sequence Clustering &#40;Analysis Services - Exploration de données&#41;](mining-model-content-for-sequence-clustering-models.md).  
  
## <a name="creating-predictions"></a>Création de prédictions  
 Après l'apprentissage d'un modèle, les résultats sont stockés sous la forme d'un jeu de modèles. Vous pouvez utiliser les descriptions des séquences les plus courantes dans les données pour prévoir l'étape probable suivante d'une nouvelle séquence. Toutefois, comme l'algorithme inclut d'autres colonnes, vous pouvez utiliser le modèle obtenu pour identifier les relations entre les données en séquence et les entrées non séquentielles. Par exemple, si vous ajoutez des données démographiques au modèle, vous pouvez effectuer des prévisions sur des groupes spécifiques de clients. Les requêtes de prédiction peuvent être personnalisées pour retourner un nombre variable de prédictions ou des statistiques descriptives.  
  
 Pour plus d’informations sur la façon de créer des requêtes sur un modèle d’exploration de données, consultez [Requêtes d’exploration de données](data-mining-queries.md). Pour obtenir des exemples d’utilisation de requêtes avec un modèle Sequence Clustering, consultez [Exemples de requêtes de modèle MSC (Sequence Clustering)](clustering-model-query-examples.md).  
  
## <a name="remarks"></a>Notes  
  
-   Ne prend pas en charge l’utilisation du langage PMML (Predictive Model Markup Language) pour créer des modèles d’exploration de données.  
  
-   Prend en charge l’extraction.  
  
-   Prend en charge l'utilisation de modèles d'exploration de données OLAP et la création de dimensions d'exploration de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Références techniques relatives à l’algorithme MSC (Microsoft Sequence Clustering)](microsoft-sequence-clustering-algorithm-technical-reference.md)   
 [Exemples de requêtes de modèle MSC (Sequence Clustering)](clustering-model-query-examples.md)   
 [Explorer un modèle à l’aide de la visionneuse de l’algorithme MSC (Microsoft Sequence Cluster)](browse-a-model-using-the-microsoft-sequence-cluster-viewer.md)  
  
  
