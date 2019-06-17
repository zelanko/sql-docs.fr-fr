---
title: Conception d’agrégations (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- statistical information [XML for Analysis]
- batches [XML for Analysis]
- aggregations [Analysis Services], XML for Analysis
- XMLA, aggregations
- queries [XMLA]
- XML for Analysis, aggregations
- iterative aggregation process [XMLA]
ms.assetid: 4dd27afa-10c7-408d-bc24-ca74217ddbcb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81450789395dfef84f81896990fa251514d3489e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62702119"
---
# <a name="designing-aggregations-xmla"></a>Conception d'agrégations (XMLA)
  Les conceptions d'agrégation sont associées aux partitions d'un groupe de mesures particulier pour s'assurer que les partitions utilisent la même structure lors du stockage d'agrégations. À l’aide de la même structure de stockage pour les partitions vous permet de vous permet de définir facilement des partitions qui peuvent être fusionnées ultérieurement à l’aide de la [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) commande. Pour plus d’informations sur les conceptions d’agrégation, consultez [agrégations et conceptions d’agrégation](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
 Pour définir des agrégations pour une conception d’agrégation, vous pouvez utiliser la [DesignAggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) commande XML for Analysis (XMLA). La commande `DesignAggregations` possède des propriétés qui identifient la conception d'agrégation à utiliser comme référence et la façon dont est contrôlé le processus de conception basé sur cette référence. Par le biais de la commande `DesignAggregations` et de ses propriétés, vous pouvez concevoir des agrégations de manière itérative ou par lot, puis consulter les statistiques de conception obtenues pour évaluer le processus de conception.  
  
## <a name="specifying-an-aggregation-design"></a>Définition d'une conception d'agrégation  
 Le [objet](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) propriété de la `DesignAggregations` commande doit contenir une référence d’objet à une conception d’agrégation existante. La référence d'objet contient un identificateur de base de données, un identificateur de cube, un identificateur de groupe de mesures et un identificateur de conception d'agrégation. Si la conception d'agrégation n'existe pas déjà, une erreur se produit.  
  
## <a name="controlling-the-design-process"></a>Contrôle du processus de conception  
 Vous pouvez utiliser les propriétés de la commande `DesignAggregations` décrites ci-dessous pour contrôler l'algorithme utilisé pour définir des agrégations pour la conception d'agrégation :  
  
-   Le [étapes](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/steps-element-xmla) propriété détermine le nombre d’itérations le `DesignAggregations` commande doit prendre avant de retourner le contrôle à l’application cliente.  
  
-   Le [temps](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/time-element-xmla) propriété détermine le nombre de millisecondes le `DesignAggregations` commande doit prendre avant de retourner le contrôle à l’application cliente.  
  
-   Le [optimisation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/optimization-element-xmla) propriété détermine le pourcentage estimé d’amélioration des performances la `DesignAggregations` commande doit essayer d’atteindre. Si vous concevez des agrégations de manière itérative, vous n'avez besoin d'envoyer cette propriété que dans la première commande.  
  
-   Le [stockage](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/storage-element-xmla) propriété détermine la quantité estimée de stockage sur disque, en octets, utilisée par le `DesignAggregations` commande. Si vous concevez des agrégations de manière itérative, vous n'avez besoin d'envoyer cette propriété que dans la première commande.  
  
-   Le [matérialiser](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/materialize-element-xmla) propriété détermine si le `DesignAggregations` commande doit créer les agrégations définies pendant le processus de conception. Si vous concevez des agrégations de manière itérative, cette propriété doit être définie à false tant que vous n'êtes pas prêt à enregistrer les agrégations conçues. Lorsqu'elle est définie à true, le processus de conception en cours prend fin et les agrégations définies sont ajoutées à la conception d'agrégation spécifiée.  
  
## <a name="specifying-queries"></a>Définition de la propriété Queries  
 La commande DesignAggregations prend en charge la commande de l’optimisation de l’utilisation en incluant un ou plusieurs `Query` éléments dans le [requêtes](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/queries-element-xmla) propriété. Le `Queries` propriété peut contenir un ou plusieurs [requête](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/query-element-xmla) éléments. Si la propriété `Queries` ne contient pas d'éléments `Query`, la conception d'agrégation spécifiée dans l'élément `Object` utilise une structure par défaut qui contient un ensemble général d'agrégations. Cet ensemble général d'agrégations vise à répondre aux critères spécifiés dans les propriétés `Optimization` et `Storage` de la commande `DesignAggregations`.  
  
 Chaque élément `Query` représente une requête d'objectif que le processus de conception utilise pour définir des agrégations qui visent les requêtes utilisées le plus fréquemment. Vous pouvez spécifier vos propres requêtes d’objectif, ou vous pouvez utiliser les informations stockées par une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans le journal des requêtes pour récupérer des informations sur les plus fréquemment les requêtes utilisées. L'Assistant Optimisation de l'utilisation utilise le journal des requêtes pour récupérer les requêtes d'objectif en fonction du temps, de l'utilisation ou d'un utilisateur spécifié lors de l'envoi d'une commande `DesignAggregations`. Pour plus d’informations, consultez [basée sur l’utilisation de l’optimisation Assistant F1 Aide](../usage-based-optimization-wizard-f1-help.md).  
  
 Si vous créez des agrégations de manière itérative, vous ne devez passer de requêtes d'objectif que dans la première commande `DesignAggregations` parce que l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stocke ces requêtes d'objectif et les utilise pendant les commandes `DesignAggregations` suivantes. Une fois les requêtes d'objectif passées dans la première commande `DesignAggregations` d'un procédé itératif, toute commande `DesignAggregations` suivante qui contient des requêtes d'objectif dans la propriété `Queries` génère une erreur.  
  
 L'élément `Query` contient une valeur délimitée par des virgules qui renferme les arguments suivants :  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Fréquence*  
 Un facteur de pondération qui correspond au nombre de fois que la requête a été exécutée antérieurement. Si le `Query` élément représente une nouvelle requête, le *fréquence* valeur représente le facteur de pondération utilisé par le processus de conception pour évaluer la requête. À mesure que la valeur de la fréquence s'accroît, le poids associé à la requête pendant le processus de conception augmente.  
  
 *Dataset*  
 Une chaîne numérique qui spécifie quels attributs d'une dimension doivent être inclus dans la requête. Cette chaîne doit comporter autant de caractères que la dimension compte d'attributs. Zéro (0) indique que l'attribut à la position ordinale spécifiée n'est pas inclus dans la requête pour la dimension spécifiée, alors qu'un (1) indique que l'attribut à la position ordinale spécifiée est inclus dans la requête pour la dimension spécifiée.  
  
 Par exemple, la chaîne  « 011 » se rapporte à une requête concernant une dimension à trois attributs, dont le deuxième et le troisième sont inclus dans la requête.  
  
> [!NOTE]  
>  Certains attributs, qualifiés d'exclus, ne sont pas pris en compte dans le dataset. Pour plus d’informations sur les attributs exclus, consultez [élément de requête &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/query-element-xmla).  
  
 Chaque dimension du groupe de mesures qui contient la conception d’agrégation est représentée par un *Dataset* valeur dans le `Query` élément. L'ordre des valeurs *Dataset* doit correspondre à celui des dimensions incluses dans le groupe de mesures.  
  
## <a name="designing-aggregations-using-iterative-or-batch-processes"></a>Conception d'agrégations au moyen d'un processus de traitement itératif ou par lots  
 Vous pouvez utiliser la commande `DesignAggregations` dans le cadre d'un processus de traitement itératif ou par lots, selon le degré d'interactivité exigé par le processus de conception.  
  
### <a name="designing-aggregations-using-an-iterative-process"></a>Conception d'agrégations au moyen d'un processus de traitement itératif  
 Pour concevoir des agrégations de manière itérative, vous devez envoyer plusieurs commandes `DesignAggregations` de façon à fournir un contrôle précis sur le processus de conception. L'Assistant Conception d'agrégation utilise cette même approche pour fournir un contrôle précis sur le processus de conception. Pour plus d’informations, consultez [d’agrégation conception Assistant F1](../aggregation-design-wizard-f1-help.md).  
  
> [!NOTE]  
>  Une session explicite est nécessaire pour concevoir des agrégations de manière itérative. Pour plus d’informations sur les sessions explicites, consultez [gestion des connexions et Sessions &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md).  
  
 Pour lancer le processus de traitement itératif, vous devez commencer par envoyer une commande `DesignAggregations` contenant les informations suivantes :  
  
-   les valeurs des propriétés `Storage` et `Optimization` sur lesquelles porte l'ensemble du processus de conception ;  
  
-   les valeurs des propriétés `Steps` et `Time` sur lesquelles se limite la première étape du processus de conception ;  
  
-   si vous souhaitez recourir à l'optimisation basée sur l'utilisation, la propriété `Queries` qui contient les requêtes d'objectif sur lesquelles porte l'ensemble du processus de conception ;  
  
-   la propriété `Materialize` définie à false. La définition de cette propriété à false indique que le processus de conception n'enregistre pas les agrégations définies dans la conception d'agrégation lorsque la commande aboutit.  
  
 Lorsque la première commande `DesignAggregations` aboutit, elle retourne un ensemble de lignes qui contient des statistiques de conception. Vous pouvez évaluer ces statistiques pour déterminer si le processus de conception doit continuer ou s'il est terminé. Si le processus doit continuer, vous devez envoyer une autre commande `DesignAggregations` qui contient les valeurs `Steps` et `Time` auxquelles se limite cette étape du processus de conception. Vous évaluez ensuite les statistiques obtenues et vous déterminez si le processus de conception doit continuer. Ce processus itératif d'envoi de commandes `DesignAggregations` et d'évaluation des résultats se poursuit tant que vous n'avez pas atteint vos objectifs et que vous n'avez pas défini un ensemble d'agrégations approprié.  
  
 Une fois que vous être satisfait de l'ensemble d'agrégations, vous devez envoyer une dernière commande `DesignAggregations`. La propriété `DesignAggregations` de cette commande finale `Steps` doit avoir la valeur 1, tandis que sa propriété `Materialize` doit être définie à true. En utilisant ces paramètres, cette dernière commande `DesignAggregations` met fin au processus de conception et enregistre l'agrégation définie dans la conception d'agrégation.  
  
### <a name="designing-aggregations-using-a-batch-process"></a>Conception d'agrégations au moyen d'un processus de traitement par lots  
 Vous pouvez également concevoir des agrégations dans un processus de traitement par lots en envoyant une commande `DesignAggregations` unique qui contient les valeurs des propriétés `Steps`, `Time`, `Storage` et `Optimization` sur lesquelles porte et se limite l'ensemble du processus de conception. Si vous souhaitez recourir à l'optimisation basée sur l'utilisation, les requêtes d'objectif sur lesquelles porte le processus de conception doivent également être incluses dans la propriété `Queries`. De même, veillez à ce que la propriété `Materialize` soit définie à true pour que le processus de conception enregistre les agrégations définies dans la conception d'agrégation dès que la commande aboutit.  
  
 Vous pouvez concevoir des agrégations en utilisant un processus de traitement par lots dans le cadre d'une session implicite ou explicite. Pour plus d’informations sur les sessions implicites et explicites, consultez [gestion des connexions et Sessions &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md).  
  
## <a name="returning-design-statistics"></a>Retour des statistiques de conception  
 Au moment où la commande `DesignAggregations` restitue le contrôle à l'application cliente, elle retourne un ensemble de lignes tenant sur une seule ligne qui représente les statistiques de conception pour la commande. Cet ensemble de lignes se compose des colonnes répertoriées dans le tableau suivant.  
  
|colonne|Data type|Description|  
|------------|---------------|-----------------|  
|Étapes|Entier|Nombre d'étapes parcourues par la commande avant de restituer le contrôle à l'application cliente.|  
|Time|Entier long|Temps en millisecondes nécessaire à la commande pour restituer le contrôle à l'application cliente.|  
|Optimization|Double|Estimation du pourcentage d'amélioration des performances atteint par la commande avant de restituer le contrôle à l'application cliente.|  
|Stockage|Entier long|Estimation du nombre d'octets nécessaires à la commande pour restituer le contrôle à l'application cliente.|  
|Aggregations|Entier long|Nombre d'agrégations définies par la commande avant de restituer le contrôle à l'application cliente.|  
|LastStep|Booléen|Indique si les données contenues dans l'ensemble de lignes correspondent à la dernière étape du processus de conception. Si la propriété `Materialize` de la commande a été définie à true, la valeur de cette colonne est définie à true.|  
  
 Vous pouvez utiliser les statistiques de conception contenues dans l'ensemble de lignes après chaque commande `DesignAggregations`, que ce soit dans le cadre d'une conception itérative ou dans celui d'une conception par lots. Dans le cadre d'une conception itérative, vous pouvez utiliser les statistiques de conception pour déterminer et afficher l'état d'avancement. Lorsque vous concevez des agrégations par lots, vous pouvez utiliser les statistiques de conception pour déterminer le nombre d'agrégations créés par la commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
