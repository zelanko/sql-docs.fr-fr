---
title: Vue d’ensemble de l’extensibilité des règles d’analyse du code de base de données | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 62f5c980-18d5-43fe-b443-c9e149d01fc7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 42896bb62b5566c955c86c43618a8f64e4968b5a
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52405866"
---
# <a name="overview-of-extensibility-for-database-code-analysis-rules"></a>Vue d'ensemble de l'extensibilité pour les règles d'analyse du code de base de données
Les éditions de Visual Studio contenant SQL Server Data Tools comportent des règles d’analyse du code permettant de générer des rapports sur les avertissements de conception, d’affectation de noms et de performances de Transact\-SQL dans le code de la base de données. Pour plus d’informations, voir [Analyser le code de la base de données pour améliorer la qualité du code](https://msdn.microsoft.com/library/dd172133(v=vs.100).aspx).  
  
Si les règles d’analyse du code intégrées ne couvrent pas un problème Transact\-SQL que vous souhaitez inclure, vous pouvez créer des règles personnalisées d’analyse du code de base de données. Vous pouvez, par exemple, créer une règle personnalisée qui évite d’utiliser l’instruction WAITFOR DELAY, comme dans [Procédure de création d’un assembly de règle personnalisée d’analyse du code statique pour SQL Server](../ssdt/walkthrough-author-custom-static-code-analysis-rule-assembly.md). Pour créer des règles personnalisées d’analyse du code de base de données, utilisez les classes de l’espace de noms [CodeAnalysis](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.codeanalysis.aspx).  
  
Avant de créer des règles d'analyse du code personnalisées, vous devez comprendre l'architecture de base des différents composants des règles d'analyse du code de base de données.  
  
## <a name="database-code-analysis-rules-components"></a>Composants des règles d'analyse du code de base de données  
Le diagramme suivant illustre l'interaction entre les composants de règles d'analyse du code de base de données :  
  
![Composants des règles d’analyse du code de base de données](../ssdt/media/ssdt-database-code-analysis-rules-components.jpg "Composants des règles d’analyse du code de base de données")  
  
Quand vous utilisez la fonctionnalité d’analyse du code de base de données, soit en exécutant directement l’analyse du code statique (pour plus d’informations, voir [Guide pratique : Analyser du code Transact-SQL afin de détecter des défauts](https://msdn.microsoft.com/library/dd172119(v=vs.100).aspx)), soit en effectuant une génération, toutes les règles sont chargées et utilisées selon la manière dont vous les avez configurées dans votre projet. Pour plus d’informations, voir [Guide pratique : Activer et désactiver des règles spécifiques pour l’analyse statique du code d’une base de données](https://msdn.microsoft.com/library/dd172131(v=vs.100).aspx). Le Gestionnaire d'extensions charge également les éventuels assemblys de règles personnalisées que vous avez créés et enregistrés. Pour plus d’informations, voir [Guide pratique : Installer et gérer des extensions de fonctionnalités](../ssdt/how-to-install-and-manage-feature-extensions.md).  
  
Une classe de règle personnalisée d’analyse du code hérite de [SqlCodeAnalysisRule](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.codeanalysis.sqlcodeanalysisrule.aspx). La classe de règle personnalisée peut accéder à plusieurs objets utiles via son contexte d'exécution de règle, notamment :  
  
-   Des métadonnées relatives à la règle elle-même.  
  
-   Le modèle Dac.Model.TSqlModel représentant le schéma de la base de données, y compris tous les éléments de modèle, les relations qu’ils entretiennent et toutes les propriétés des éléments.  
  
-   Pour les règles qui examinent des éléments spécifiques, l’objet Dac.Model.TSqlObject représentant cet élément de schéma dans le modèle est inclus dans le contexte.  
  
-   De nombreux objets de schéma ont également une représentation [ScriptDom](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.aspx) accessible par le biais de ce contexte. Il s’agit d’une représentation AST d’un élément qui peut être utile pour voir les éventuels problèmes de syntaxe, comme la présence de [SelectStarExpression](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.selectstarexpression.aspx).  
  
Un élément Dac.CodeAnalysis.SqlRuleProblem est créé par la règle pour représenter tous les problèmes qu’elle a détectés. Lors de cette création, l’objet Dac.Model.TSqlObject correspondant et éventuellement un élément de représentation [ScriptDom](https://msdn.microsoft.com/library/microsoft.sqlserver.transactsql.scriptdom.aspx) sont passés au constructeur et utilisés pour déterminer l’emplacement du problème dans les fichiers de code source. À la fin de l'analyse, tous ces problèmes sont transmis au gestionnaire d'erreurs et affichés dans la liste d'erreurs.  
  
## <a name="see-also"></a> Voir aussi  
[Extension des fonctionnalités de base de données](../ssdt/extending-the-database-features.md)  
  
