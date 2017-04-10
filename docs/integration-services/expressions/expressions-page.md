---
title: "Page Expressions | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.expressionspage.f1"
helpviewer_keywords: 
  - "Page Expressions, boîte de dialogue"
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
caps.latest.revision: 17
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 17
---
# Page Expressions
  Utilisez la page **Expressions** pour modifier les expressions de propriété et pour accéder aux boîtes de dialogue **Éditeur d’expressions de la propriété** et **Générateur d’expressions**.  
  
 Les expressions de propriété mettent à jour les valeurs des propriétés lors de l'exécution du package. Ces expressions peuvent être utilisées avec les propriétés des packages, des tâches, des conteneurs, des gestionnaires de connexions ainsi que certains composants de flux de données. Les expressions sont évaluées et leurs résultats sont utilisés à la place des valeurs auxquelles vous appliquez les propriétés lorsque vous avez configuré le package et les objets de package. Les expressions peuvent inclure des variables et les fonctions et les opérateurs fournis par le langage d'expression. Par exemple, vous pouvez générer la ligne Objet pour la tâche d'envoi de courrier en concaténant la valeur d'une variable qui contient la chaîne « prévisions météorologiques pour » et les résultats de retour de la fonction GETDATE() pour obtenir la chaîne « Prévisions météorologiques pour le 5/4/2006 ».  
  
 Pour en savoir plus sur l’utilisation des expressions de propriété et l’écriture d’expressions, consultez [Expressions Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md) et [Expressions de propriété dans des packages](../../integration-services/expressions/use-property-expressions-in-packages.md).  
  
## Options  
 **Expressions (…)**  
 Cliquez sur les points de suspension pour ouvrir la boîte de dialogue **Éditeur d’expressions de la propriété**. Pour plus d’informations, consultez [Éditeur d’expressions de la propriété](../../integration-services/expressions/property-expressions-editor.md).  
  
 **\<nom de propriété>**  
 Cliquez sur les points de suspension pour ouvrir la boîte de dialogue **Générateur d'expression** . Pour plus d'informations, consultez [Expression Builder](../../integration-services/expressions/expression-builder.md).  
  
## Voir aussi  
 [Variables Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md)   
 [Variables système](../../integration-services/system-variables.md)   
 [Expressions Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  