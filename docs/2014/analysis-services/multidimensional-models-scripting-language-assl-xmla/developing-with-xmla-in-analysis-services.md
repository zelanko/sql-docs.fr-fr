---
title: Développer avec XMLA dans les services d’analyse ( Microsoft Docs
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
ms.openlocfilehash: 27b143a9cc5c888c6e464d300d2ccfea114ef9bc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2020
ms.locfileid: "80380680"
---
# <a name="developing-with-xmla-in-analysis-services"></a>Développement avec XMLA dans Analysis Services
  XMLA (XML for Analysis) est un protocole XML basé sur SOAP (Simple Object Access Protocol) conçu spécifiquement pour offrir un accès universel à n'importe quelle source de données multidimensionnelle standard accessible via une connexion HTTP. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise XMLA comme seul protocole pour communiquer avec les applications clientes. Fondamentalement, toutes les bibliothèques clientes prises en charge par Analysis Services formulent des demandes et des réponses XMLA.  
  
 En tant que développeur, vous pouvez utiliser XMLA pour intégrer une application cliente à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], sans aucune dépendance du .NET Framework ou des interfaces COM. La configuration requise pour une application qui inclut l'hébergement sur un large éventail de plateformes peut être satisfaite à l'aide de XMLA et d'une connexion HTTP à [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] est entièrement conforme à la spécification 1.1 XMLA, mais l'étend également pour permettre la définition de données, la manipulation des données et la prise en charge du contrôle de données. Les extensions Analysis Services sont désignées par le terme ASSL (Analysis Services Scripting Language). L'utilisation de XMLA et d'ASSL autorise un plus large ensemble de fonctionnalités que celui fournit par XMLA. Pour plus d’informations sur ASSL, voir [Developing with Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Gestion des connexions et des sessions &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md)|Explique comment se connecter à une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et comment gérer les sessions et la conservation de l'état avec XMLA.|  
|[Manipulation Des erreurs et des avertissements &#40;&#41;XMLA](handling-errors-and-warnings-xmla.md)|Indique comment [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retourne les informations d'erreur et d'avertissement pour les méthodes et les commandes XMLA.|  
|[Définir et identifier les objets &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)|Décrit les identificateurs et références d'objet et explique comment les utiliser dans les commandes XMLA.|  
|[Gestion des transactions &#40;&#41;XMLA](managing-transactions-xmla.md)|Détaille comment utiliser les commandes [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla)et [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) pour définir et gérer explicitement une transaction sur la session XMLA en cours.|  
|[Annulation des commandes &#40;&#41;XMLA](../multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|Décrit comment utiliser la commande [Annuler](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)pour annuler les commandes, les sessions et les connexions dans XMLA.|  
|[Exécution des opérations de lots &#40;&#41;XMLA](performing-batch-operations-xmla.md)|Décrit comment utiliser la commande [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) pour exécuter plusieurs commandes XMLA, en série ou en parallèle, soit dans la même transaction ou comme des transactions séparées, en utilisant une seule méthode XMLA [Execute.](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)|  
|[Créer et modifier des objets &#40;&#41;XMLA](creating-and-altering-objects-xmla.md)|Décrit comment utiliser les commandes [Créer,](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) [modifier](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)et [supprimer,](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) ainsi que les éléments de langage de script des services [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] d’analyse (ASSL), définir, modifier ou supprimer des objets d’une instance.|  
|[Bases de données de verrouillage et de déblocage &#40;&#41;XMLA](locking-and-unlocking-databases-xmla.md)|Détaillez comment utiliser les commandes [De verrouillage](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) et [de déverrouillage](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) pour verrouiller et débloquer une [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de données.|  
|[Traitement d’objets &#40;XMLA&#41;](processing-objects-xmla.md)|Décrit comment utiliser la commande de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [processus](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) pour traiter un objet.|  
|[Fusion des partitions &#40;&#41;XMLA](merging-partitions-xmla.md)|Décrit comment utiliser la commande [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fusionner les partitions sur une instance.|  
|[Concevoir des agrégations &#40;XMLA&#41;](designing-aggregations-xmla.md)|Décrit comment utiliser la commande [DesignAggregations,](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) soit en mode itératif ou par lots, pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]concevoir des agrégations pour un design d’agrégation dans .|  
|[Sauvegarde, restauration et synchronisation de bases de données &#40;XMLA&#41;](backing-up-restoring-and-synchronizing-databases-xmla.md)|Explique comment utiliser les commandes [Backup](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) et [Restore](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) pour sauvegarder et restaurer une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à partir d'un fichier de sauvegarde.<br /><br /> Décrit également comment utiliser la commande [Synchronize](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla) [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour synchroniser une base de données avec une base de données existante dans la même instance ou sur un cas différent.|  
|[L’insertion, la mise à jour et l’abandon des membres &#40;&#41;XMLA](inserting-updating-and-dropping-members-xmla.md)|Décrit comment utiliser les commandes [Insert](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla), [Update](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)et [Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) pour ajouter, modifier ou supprimer les membres d’une dimension compatible avec l’écriture.|  
|[Mise à jour des cellules &#40;&#41;XMLA](updating-cells-xmla.md)|Décrit comment utiliser la commande [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) pour changer les valeurs des cellules dans une partition activée par écrit.|  
|[Gestion des caches &#40;&#41;XMLA](managing-caches-xmla.md)|Détaille comment utiliser la commande [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] effacer les caches d’objets.|  
|[Surveillance des traces &#40;&#41;XMLA](monitoring-traces-xmla.md)|Décrit comment utiliser la commande [abonnez-vous](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla) pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vous abonner et surveiller une trace existante sur une instance.|  
  
## <a name="data-mining-with-xmla"></a>Exploration de données avec XMLA  
 XML for Analysis prend entièrement en charge les ensembles de lignes de schéma d'exploration de données. Ces ensembles de lignes fournissent des informations pour interroger les modèles d’exploration de données en utilisant la méthode [Découvrir.](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) Pour plus d’informations sur les ensembles de schémas d’exploration de données, voir [Data Mining Schema Rowsets](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
 Pour plus d’informations sur DMX, voir [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference).  
  
## <a name="namespace-and-schema"></a>Espace de noms et schéma  
  
### <a name="namespace"></a>Espace de noms  
 Le schéma défini dans cette spécification utilise `https://schemas.microsoft.com/AnalysisServices/2003/Engine` l’espace de nom XML et l’abréviation standard "DDL".  
  
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
 [Développer avec des services d’analyse Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Présentation de l’architecture Microsoft OLAP](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
