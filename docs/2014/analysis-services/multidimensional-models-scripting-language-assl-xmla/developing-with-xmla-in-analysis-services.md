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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62727226"
---
# <a name="developing-with-xmla-in-analysis-services"></a>Développement avec XMLA dans Analysis Services
  XMLA (XML for Analysis) est un protocole XML basé sur SOAP (Simple Object Access Protocol) conçu spécifiquement pour offrir un accès universel à n'importe quelle source de données multidimensionnelle standard accessible via une connexion HTTP. 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise XMLA comme seul protocole pour communiquer avec les applications clientes. Fondamentalement, toutes les bibliothèques clientes prises en charge par Analysis Services formulent des demandes et des réponses XMLA.  
  
 En tant que développeur, vous pouvez utiliser XMLA pour intégrer une application cliente à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], sans aucune dépendance du .NET Framework ou des interfaces COM. La configuration requise pour une application qui inclut l'hébergement sur un large éventail de plateformes peut être satisfaite à l'aide de XMLA et d'une connexion HTTP à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est entièrement conforme à la spécification 1.1 XMLA, mais l'étend également pour permettre la définition de données, la manipulation des données et la prise en charge du contrôle de données. Les extensions Analysis Services sont désignées par le terme ASSL (Analysis Services Scripting Language). L'utilisation de XMLA et d'ASSL autorise un plus large ensemble de fonctionnalités que celui fournit par XMLA. Pour plus d’informations sur ASSL, consultez [développement avec le langage de script Analysis Services &#40;&#41;ASSL ](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Gestion des connexions et des sessions &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md)|Explique comment se connecter à une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et comment gérer les sessions et la conservation de l'état avec XMLA.|  
|[Gestion des erreurs et des avertissements &#40;XMLA&#41;](handling-errors-and-warnings-xmla.md)|Indique comment [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retourne les informations d'erreur et d'avertissement pour les méthodes et les commandes XMLA.|  
|[Définition et identification d’objets &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)|Décrit les identificateurs et références d'objet et explique comment les utiliser dans les commandes XMLA.|  
|[Gestion des transactions &#40;&#41;XMLA](managing-transactions-xmla.md)|Explique comment utiliser les commandes [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla)et [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) pour définir et gérer explicitement une transaction sur la session XMLA actuelle.|  
|[Annulation de commandes &#40;&#41;XMLA](../multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|Décrit comment utiliser la commande [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)pour annuler les commandes, les sessions et les connexions dans XMLA.|  
|[Exécution d’opérations de traitement par lots &#40;&#41;XMLA](performing-batch-operations-xmla.md)|Décrit comment utiliser la commande [batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) pour exécuter plusieurs commandes XMLA, en série ou en parallèle, dans la même transaction ou en tant que transactions distinctes, à l’aide d’une seule méthode XMLA [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) .|  
|[Création et modification d’objets &#40;XMLA&#41;](creating-and-altering-objects-xmla.md)|Décrit comment utiliser les commandes [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla), [ALTER](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)et [Delete](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) , ainsi que les éléments ASSL (Analysis Services Scripting Language), pour définir, modifier ou supprimer des objets d’une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.|  
|[Verrouillage et déverrouillage des bases de données &#40;&#41;XMLA](locking-and-unlocking-databases-xmla.md)|Explique comment utiliser les commandes [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) et [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) pour verrouiller et déverrouiller une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données.|  
|[Traitement des objets &#40;&#41;XMLA](processing-objects-xmla.md)|Décrit comment utiliser la commande [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) pour traiter un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objet.|  
|[Fusion de partitions &#40;&#41;XMLA](merging-partitions-xmla.md)|Décrit comment utiliser la commande [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) pour fusionner des partitions sur une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.|  
|[Conception d’agrégations &#40;&#41;XMLA](designing-aggregations-xmla.md)|Décrit comment utiliser la commande [DesignAggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) , en mode itératif ou par lot, pour concevoir des agrégations pour une conception d’agrégation [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]dans.|  
|[Sauvegarde, restauration et synchronisation des bases de données &#40;XMLA&#41;](backing-up-restoring-and-synchronizing-databases-xmla.md)|Explique comment utiliser les commandes [Backup](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) et [Restore](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) pour sauvegarder et restaurer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à partir d'un fichier de sauvegarde.<br /><br /> Décrit également comment utiliser la commande [Synchronize](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla) pour synchroniser une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données avec une base de données existante sur la même instance ou sur une autre instance.|  
|[Insertion, mise à jour et suppression de membres &#40;XMLA&#41;](inserting-updating-and-dropping-members-xmla.md)|Décrit comment utiliser les commandes [Insert](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla), [Update](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)et [Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) pour ajouter, modifier ou supprimer des membres d’une dimension activée en écriture.|  
|[Mise à jour de cellules &#40;XMLA&#41;](updating-cells-xmla.md)|Décrit comment utiliser la commande [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) pour modifier les valeurs des cellules dans une partition activée en écriture.|  
|[Gestion des caches &#40;XMLA&#41;](managing-caches-xmla.md)|Explique comment utiliser la commande [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) pour effacer les caches d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objets.|  
|[Suivi des suivis &#40;XMLA&#41;](monitoring-traces-xmla.md)|Décrit comment utiliser la commande [subscribe](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla) pour s’abonner à et surveiller une trace existante sur [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] une instance.|  
  
## <a name="data-mining-with-xmla"></a>Exploration de données avec XMLA  
 XML for Analysis prend entièrement en charge les ensembles de lignes de schéma d'exploration de données. Ces ensembles de lignes fournissent des informations pour interroger les modèles d’exploration de données à l’aide de la méthode [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) . Pour plus d’informations sur les ensembles de lignes de schéma d’exploration de données, consultez [ensembles de lignes de schéma d’exploration de données](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
 Pour plus d’informations sur DMX, consultez [Data Mining Extensions &#40;dmx&#41; référence](/sql/dmx/data-mining-extensions-dmx-reference).  
  
## <a name="namespace-and-schema"></a>Espace de noms et schéma  
  
### <a name="namespace"></a>Espace de noms  
 Le schéma défini dans cette spécification utilise l’espace de https://schemas.microsoft.com/AnalysisServices/2003/Engine noms XML et l’abréviation standard « DDL ».  
  
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
 [Présentation de l'architecture Microsoft OLAP](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
