---
title: Conception d’agrégations (XMLA) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b9f681b3c99bd0e8351a844f28b16be6249de199
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50147184"
---
# <a name="designing-aggregations-xmla"></a>Conception d'agrégations (XMLA)
  Les conceptions d'agrégation sont associées aux partitions d'un groupe de mesures particulier pour s'assurer que les partitions utilisent la même structure lors du stockage d'agrégations. À l’aide de la même structure de stockage pour les partitions vous permet de vous permet de définir facilement des partitions qui peuvent être fusionnées ultérieurement à l’aide de la [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) commande. Pour plus d’informations sur les conceptions d’agrégation, consultez [agrégations et conceptions d’agrégation](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
 Pour définir des agrégations pour une conception d’agrégation, vous pouvez utiliser la [DesignAggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) commande XML for Analysis (XMLA). Le **DesignAggregations** commande possède des propriétés qui identifient la conception d’agrégation à utiliser comme référence et comment contrôler le processus de conception basé sur cette référence. À l’aide de la **DesignAggregations** commande et ses propriétés, vous pouvez concevoir des agrégations itérative ou dans un lot et puis afficher les statistiques de conception obtenues pour évaluer le processus de conception.  
  
## <a name="specifying-an-aggregation-design"></a>Définition d'une conception d'agrégation  
 Le [objet](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) propriété de la **DesignAggregations** commande doit contenir une référence d’objet à une conception d’agrégation existante. La référence d'objet contient un identificateur de base de données, un identificateur de cube, un identificateur de groupe de mesures et un identificateur de conception d'agrégation. Si la conception d'agrégation n'existe pas déjà, une erreur se produit.  
  
## <a name="controlling-the-design-process"></a>Contrôle du processus de conception  
 Vous pouvez utiliser les propriétés suivantes de la **DesignAggregations** commande pour contrôler l’algorithme utilisé pour définir des agrégations pour la conception d’agrégation :  
  
-   Le [étapes](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/steps-element-xmla) propriété détermine le nombre d’itérations le **DesignAggregations** commande doit prendre avant de retourner le contrôle à l’application cliente.  
  
-   Le [temps](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/time-element-xmla) propriété détermine le nombre de millisecondes le **DesignAggregations** commande doit prendre avant de retourner le contrôle à l’application cliente.  
  
-   Le [optimisation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/optimization-element-xmla) propriété détermine le pourcentage estimé d’amélioration des performances la **DesignAggregations** commande doit essayer d’atteindre. Si vous concevez des agrégations de manière itérative, vous n'avez besoin d'envoyer cette propriété que dans la première commande.  
  
-   Le [stockage](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/storage-element-xmla) propriété détermine la quantité estimée de stockage sur disque, en octets, utilisée par le **DesignAggregations** commande. Si vous concevez des agrégations de manière itérative, vous n'avez besoin d'envoyer cette propriété que dans la première commande.  
  
-   Le [matérialiser](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/materialize-element-xmla) propriété détermine si le **DesignAggregations** commande doit créer les agrégations définies pendant le processus de conception. Si vous concevez des agrégations de manière itérative, cette propriété doit être définie à false tant que vous n'êtes pas prêt à enregistrer les agrégations conçues. Lorsqu'elle est définie à true, le processus de conception en cours prend fin et les agrégations définies sont ajoutées à la conception d'agrégation spécifiée.  
  
## <a name="specifying-queries"></a>Définition de la propriété Queries  
 La commande DesignAggregations prend en charge la commande de l’optimisation de l’utilisation en incluant un ou plusieurs **requête** éléments dans le [requêtes](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/queries-element-xmla) propriété. Le **requêtes** propriété peut contenir un ou plusieurs [requête](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/query-element-xmla) éléments. Si le **requêtes** propriété ne contient aucun **requête** éléments, la conception d’agrégation spécifiée dans le **objet** élément utilise une structure par défaut qui contient un ensemble général d’agrégations. Cet ensemble général d’agrégations vise à répondre aux critères spécifiés dans le **optimisation** et **stockage** propriétés de la **DesignAggregations** commande.  
  
 Chaque élément **Query** représente une requête d'objectif que le processus de conception utilise pour définir des agrégations qui visent les requêtes utilisées le plus fréquemment. Vous pouvez spécifier vos propres requêtes d’objectif, ou vous pouvez utiliser les informations stockées par une instance de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans le journal des requêtes pour récupérer des informations sur les plus fréquemment les requêtes utilisées. L’Assistant Optimisation basée sur l’utilisation utilise le journal des requêtes pour récupérer en temps, de l’utilisation ou d’un utilisateur spécifié lorsqu’il envoie des requêtes d’objectif un **DesignAggregations** commande. Pour plus d’informations, consultez [basée sur l’utilisation de l’optimisation Assistant F1 Aide](http://msdn.microsoft.com/library/e5f5a938-ae7c-4f4e-9416-a7f94ac82763).  
  
 Si vous créez des agrégations de manière itérative, vous ne devez passer de requêtes d'objectif que dans la première commande **DesignAggregations** parce que l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stocke ces requêtes d'objectif et les utilise pendant les commandes **DesignAggregations** suivantes. Une fois les requêtes d'objectif passées dans la première commande **DesignAggregations** d'un procédé itératif, toute commande **DesignAggregations** suivante qui contient des requêtes d'objectif dans la propriété **Queries** génère une erreur.  
  
 L'élément **Query** contient une valeur délimitée par des virgules qui renferme les arguments suivants :  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Fréquence*  
 Un facteur de pondération qui correspond au nombre de fois que la requête a été exécutée antérieurement. Si l'élément **Query** représente une nouvelle requête, la valeur *Frequency* représente le facteur de pondération utilisé par le processus de conception pour évaluer la requête. À mesure que la valeur de la fréquence s'accroît, le poids associé à la requête pendant le processus de conception augmente.  
  
 *Dataset*  
 Une chaîne numérique qui spécifie quels attributs d'une dimension doivent être inclus dans la requête. Cette chaîne doit comporter autant de caractères que la dimension compte d'attributs. Zéro (0) indique que l'attribut à la position ordinale spécifiée n'est pas inclus dans la requête pour la dimension spécifiée, alors qu'un (1) indique que l'attribut à la position ordinale spécifiée est inclus dans la requête pour la dimension spécifiée.  
  
 Par exemple, la chaîne  « 011 » se rapporte à une requête concernant une dimension à trois attributs, dont le deuxième et le troisième sont inclus dans la requête.  
  
> [!NOTE]  
>  Certains attributs, qualifiés d'exclus, ne sont pas pris en compte dans le dataset. Pour plus d’informations sur les attributs exclus, consultez [élément de requête &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/query-element-xmla).  
  
 Chaque dimension dans le groupe de mesures qui contient la conception d'agrégation est représentée par une valeur *Dataset* dans l'élément **Query** . L'ordre des valeurs *Dataset* doit correspondre à celui des dimensions incluses dans le groupe de mesures.  
  
## <a name="designing-aggregations-using-iterative-or-batch-processes"></a>Conception d'agrégations au moyen d'un processus de traitement itératif ou par lots  
 Vous pouvez utiliser la **DesignAggregations** commande en tant que partie d’un processus itératif ou d’un traitement par lots, selon le degré d’interactivité exigé par le processus de conception.  
  
### <a name="designing-aggregations-using-an-iterative-process"></a>Conception d'agrégations au moyen d'un processus de traitement itératif  
 Pour concevoir des agrégations de manière itérative, vous devez envoyer plusieurs **DesignAggregations** commandes pour fournir un contrôle précis sur le processus de conception. L'Assistant Conception d'agrégation utilise cette même approche pour fournir un contrôle précis sur le processus de conception. Pour plus d’informations, consultez [d’agrégation conception Assistant F1](http://msdn.microsoft.com/library/39e23cf1-6405-4fb6-bc14-ba103314362d).  
  
> [!NOTE]  
>  Une session explicite est nécessaire pour concevoir des agrégations de manière itérative. Pour plus d’informations sur les sessions explicites, consultez [gestion des connexions et Sessions &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).  
  
 Pour démarrer le processus itératif, vous commencez par envoyer un **DesignAggregations** commande qui contient les informations suivantes :  
  
-   Le **stockage** et **optimisation** valeurs des propriétés sur lesquelles porte le processus d’ensemble de la conception.  
  
-   Le **étapes** et **temps** les valeurs de propriété sur laquelle la première étape du processus de conception est limitée.  
  
-   Si vous souhaitez que l’optimisation basée sur l’utilisation, le **requêtes** requêtes de propriété qui contient l’objectif sur lesquelles porte le processus d’ensemble de la conception.  
  
-   Le **matérialiser** propriété définie sur false. La définition de cette propriété à false indique que le processus de conception n'enregistre pas les agrégations définies dans la conception d'agrégation lorsque la commande aboutit.  
  
 Lors de la première **DesignAggregations** commande terminée, la commande retourne un ensemble de lignes qui contient des statistiques de conception. Vous pouvez évaluer ces statistiques pour déterminer si le processus de conception doit continuer ou s'il est terminé. Si le processus doit continuer, vous envoyez ensuite un autre **DesignAggregations** commande qui contient le **étapes** et **temps** valeurs avec laquelle cette étape de la conception de processus est limité. Vous évaluez ensuite les statistiques obtenues et vous déterminez si le processus de conception doit continuer. Ce processus itératif d’envoi **DesignAggregations** commandes et évaluer les résultats se poursuit jusqu'à ce que vous atteindre vos objectifs et possèdent un ensemble approprié des agrégations définies.  
  
 Une fois que vous avez atteint le jeu d’agrégations que vous le souhaitez, vous envoyez une dernière **DesignAggregations** commande. Cette dernière **DesignAggregations** commande doit avoir son **étapes** propriété définie sur 1 et ses **matérialiser** propriété définie sur true. À l’aide de ces paramètres, cette dernière **DesignAggregations** commande termine le processus de conception et enregistre l’agrégation définie à la conception d’agrégation.  
  
### <a name="designing-aggregations-using-a-batch-process"></a>Conception d'agrégations au moyen d'un processus de traitement par lots  
 Vous pouvez également concevoir des agrégations dans un traitement par lots en envoyant un seul **DesignAggregations** commande qui contient le **étapes**, **temps**, **stockage** , et **optimisation** les valeurs de propriété porte et se limite à laquelle le processus d’ensemble de la conception. Si vous souhaitez que l’optimisation basée sur l’utilisation, les requêtes d’objectif sur lequel le processus de conception est ciblé doivent également être inclus dans le **requêtes** propriété. Assurez-vous également que le **matérialiser** propriété est définie sur true, afin que le processus de conception enregistre les agrégations définies dans la conception d’agrégation à l’issue de la commande.  
  
 Vous pouvez concevoir des agrégations en utilisant un processus de traitement par lots dans le cadre d'une session implicite ou explicite. Pour plus d’informations sur les sessions implicites et explicites, consultez [gestion des connexions et Sessions &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).  
  
## <a name="returning-design-statistics"></a>Retour des statistiques de conception  
 Lorsque le **DesignAggregations** commande retourne le contrôle à l’application cliente, la commande retourne un ensemble de lignes qui contient une ligne unique qui représente les statistiques de conception pour la commande. Cet ensemble de lignes se compose des colonnes répertoriées dans le tableau suivant.  
  
|colonne|Data type|Description|  
|------------|---------------|-----------------|  
|Étapes|Entier|Nombre d'étapes parcourues par la commande avant de restituer le contrôle à l'application cliente.|  
|Time|Entier long|Temps en millisecondes nécessaire à la commande pour restituer le contrôle à l'application cliente.|  
|Optimization|Double|Estimation du pourcentage d'amélioration des performances atteint par la commande avant de restituer le contrôle à l'application cliente.|  
|Stockage|Entier long|Estimation du nombre d'octets nécessaires à la commande pour restituer le contrôle à l'application cliente.|  
|Aggregations|Entier long|Nombre d'agrégations définies par la commande avant de restituer le contrôle à l'application cliente.|  
|LastStep|Booléen|Indique si les données contenues dans l'ensemble de lignes correspondent à la dernière étape du processus de conception. Si le **matérialiser** propriété de la commande a été définie sur true, la valeur de cette colonne est définie sur true.|  
  
 Vous pouvez utiliser les statistiques de conception qui sont contenus dans l’ensemble de lignes retourné après chaque **DesignAggregations** commande itérative et conception par lots. Dans le cadre d'une conception itérative, vous pouvez utiliser les statistiques de conception pour déterminer et afficher l'état d'avancement. Lorsque vous concevez des agrégations par lots, vous pouvez utiliser les statistiques de conception pour déterminer le nombre d'agrégations créés par la commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement avec XMLA dans Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
