---
title: Développement avec XMLA dans Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, data mining
- commands [XML for Analysis]
- data mining [XML for Analysis]
- XMLA, data mining
- XML for Analysis, Analysis Services tasks
- XMLA, Analysis Services tasks
ms.assetid: 54445ee7-720c-4683-99a6-e75b3dcca904
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 00cb50fe4c71ad853e88ebd86b0891ca4bc24604
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62727226"
---
# <a name="developing-with-xmla-in-analysis-services"></a>Développement avec XMLA dans Analysis Services
  XMLA (XML for Analysis) est un protocole XML basé sur SOAP (Simple Object Access Protocol) conçu spécifiquement pour offrir un accès universel à n'importe quelle source de données multidimensionnelle standard accessible via une connexion HTTP. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise XMLA comme seul protocole pour communiquer avec les applications clientes. Fondamentalement, toutes les bibliothèques clientes prises en charge par Analysis Services formulent des demandes et des réponses XMLA.  
  
 En tant que développeur, vous pouvez utiliser XMLA pour intégrer une application cliente à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], sans aucune dépendance du .NET Framework ou des interfaces COM. La configuration requise pour une application qui inclut l'hébergement sur un large éventail de plateformes peut être satisfaite à l'aide de XMLA et d'une connexion HTTP à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est entièrement conforme à la spécification 1.1 XMLA, mais l'étend également pour permettre la définition de données, la manipulation des données et la prise en charge du contrôle de données. Les extensions Analysis Services sont désignées par le terme ASSL (Analysis Services Scripting Language). L'utilisation de XMLA et d'ASSL autorise un plus large ensemble de fonctionnalités que celui fournit par XMLA. Pour plus d’informations sur ASSL, consultez [développement avec Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Gestion des connexions et Sessions &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md)|Explique comment se connecter à une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et comment gérer les sessions et la conservation de l'état avec XMLA.|  
|[Gestion des erreurs et avertissements &#40;XMLA&#41;](handling-errors-and-warnings-xmla.md)|Indique comment [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retourne les informations d'erreur et d'avertissement pour les méthodes et les commandes XMLA.|  
|[Définition et identification d’objets &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)|Décrit les identificateurs et références d'objet et explique comment les utiliser dans les commandes XMLA.|  
|[Gestion des Transactions &#40;XMLA&#41;](managing-transactions-xmla.md)|Explique comment utiliser le [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla), et [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) commandes pour définir explicitement et gérer une transaction sur le code XMLA en cours session.|  
|[Annulation de commandes &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|Décrit comment utiliser le [Annuler](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)commande pour annuler des commandes, les sessions et connexions dans XMLA.|  
|[Exécution d’opérations de traitement par lots &#40;XMLA&#41;](performing-batch-operations-xmla.md)|Décrit comment utiliser le [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) commande à exécuter XMLA plusieurs commandes, en série ou en parallèle, dans la même transaction ou en tant que transactions distinctes, à l’aide d’un seul XMLA [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) (méthode).|  
|[Création et modification d’objets &#40;XMLA&#41;](creating-and-altering-objects-xmla.md)|Décrit comment utiliser le [créer](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla), [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla), et [supprimer](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) commandes, ainsi que des éléments Analysis Services Scripting Language (ASSL), pour définir, modifier ou supprimer objets à partir d’un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.|  
|[Verrouillage et déverrouillage de bases de données &#40;XMLA&#41;](locking-and-unlocking-databases-xmla.md)|Explique comment utiliser le [verrou](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) et [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) commandes pour verrouiller et déverrouiller une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données.|  
|[Traitement d’objets &#40;XMLA&#41;](processing-objects-xmla.md)|Décrit comment utiliser le [processus](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) commande au processus un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objet.|  
|[Fusion de Partitions &#40;XMLA&#41;](merging-partitions-xmla.md)|Décrit comment utiliser le [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) commande pour fusionner des partitions sur un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.|  
|[Conception d’agrégations &#40;XMLA&#41;](designing-aggregations-xmla.md)|Décrit comment utiliser le [DesignAggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) commande, soit dans itératif ou en mode batch, pour concevoir des agrégations pour une conception d’agrégation dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Sauvegarde, restauration et synchronisation de bases de données &#40;XMLA&#41;](backing-up-restoring-and-synchronizing-databases-xmla.md)|Décrit comment utiliser le [sauvegarde](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) et [restaurer](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) commandes pour sauvegarder et restaurer un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données à partir d’un fichier de sauvegarde.<br /><br /> Décrit également comment utiliser le [synchroniser](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla) commande pour synchroniser un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données avec une base de données existante sur la même instance ou sur une autre instance.|  
|[Insertion, mise à jour et suppression de membres &#40;XMLA&#41;](inserting-updating-and-dropping-members-xmla.md)|Décrit comment utiliser le [insérer](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla), [mise à jour](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla), et [Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) commandes pour ajouter, modifier ou supprimer des membres dans une dimension activée en écriture.|  
|[La mise à jour de cellules &#40;XMLA&#41;](updating-cells-xmla.md)|Décrit comment utiliser le [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) commande pour modifier les valeurs des cellules dans une partition activée en écriture.|  
|[Gestion des Caches &#40;XMLA&#41;](managing-caches-xmla.md)|Explique comment utiliser le [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) commande pour effacer les caches de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objets.|  
|[Surveillance de Traces &#40;XMLA&#41;](monitoring-traces-xmla.md)|Décrit comment utiliser le [s’abonner](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla) commande pour s’abonner et surveiller une trace existante sur un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.|  
  
## <a name="data-mining-with-xmla"></a>Exploration de données avec XMLA  
 XML for Analysis prend entièrement en charge les ensembles de lignes de schéma d'exploration de données. Ces ensembles de lignes fournissent des informations pour l’interrogation des modèles d’exploration de données à l’aide de la [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) (méthode). Pour plus d’informations sur les ensembles de lignes de schéma de données d’exploration de données, consultez [Data Mining Schema Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
 Pour plus d’informations sur DMX, consultez [Data Mining Extensions &#40;DMX&#41; référence](/sql/dmx/data-mining-extensions-dmx-reference).  
  
## <a name="namespace-and-schema"></a>Espace de noms et schéma  
  
### <a name="namespace"></a>Espace de noms  
 Le schéma défini dans cette spécification utilise l’espace de noms XML https://schemas.microsoft.com/AnalysisServices/2003/Engine et l’abréviation standard « DDL ».  
  
### <a name="schema"></a>schéma  
 La définition d'un schéma XSD (XML Schema definition language) pour le langage de définition d'objet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] repose sur la définition des éléments et de la hiérarchie de schéma de cette section.  
  
## <a name="extensibility"></a>Extensibilité  
 L'extensibilité du schéma du langage de définition d'objet est fournie au moyen d'un élément `Annotation` inclus dans tous les objets. Cet élément peut contenir du code XML valide issu d'un espace de noms XML (différent de l'espace de noms cible qui définit le langage de définition de données), soumis aux règles suivantes :  
  
-   Les données XML peuvent contenir uniquement des éléments.  
  
-   Chaque élément doit avoir un nom unique. Il est préférable que la valeur de `Name` fasse référence à l'espace de noms cible.  
  
 Ces règles sont imposées afin que le contenu de la balise `Annotation` puisse être exposé comme un ensemble de paires Nom/Valeur via DSO (Decision Support Objects) 9.0.  
  
 Il se peut que les commentaires et l'espace blanc contenus dans la balise `Annotation` qui ne sont pas compris dans un élément enfant ne soient pas conservés. De plus, tous les éléments doivent être accessibles en lecture-écriture ; les éléments en lecture seule sont ignorés.  
  
 Le schéma du langage de définition d'objet est figé dans le sens où le serveur ne permet pas la substitution des éléments définis dans le schéma par des types dérivés. Par conséquent, le serveur n'accepte que l'ensemble d'éléments définis ici et pas les autres éléments ou attributs. En présence d'éléments inconnus, le moteur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] génère une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement avec le langage de script Analysis Services &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Présentation de l’architecture Microsoft OLAP](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
