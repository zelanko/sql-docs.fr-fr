---
title: "Implémentation d’une classe de commande pour une Extension de traitement de données | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: b601aa43ecce5347f7229999455360be761f3bd3
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a>Implémentation d'une classe Command pour une extension pour le traitement des données
  Le **commande** objet formule une demande et le transmet à la source de données. Le texte de la commande peut prendre de nombreuses formes syntaxiques, notamment texte et XML. Si les résultats sont retournés, le **commande** objet retourne les résultats sous une **DataReader** objet.  
  
 Pour créer un **commande** classe, implémentez <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>. Implémentez la <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> méthode pour retourner un résultat défini comme un **DataReader** objet. Le <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> méthode de votre **commande** classe doit inclure une implémentation qui prend un <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> énumération en tant qu’argument. Si vous déployez votre extension pour le traitement des données sur le Concepteur de rapports, vous devez inclure une implémentation qui gère un cas <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> dans la méthode <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>. Une implémentation de type schéma uniquement est utilisée pour fournir une liste de champs au Concepteur de rapports. Le **DataReader** objet retourné par la <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> (méthode) doit contenir des informations de type et le nom des champs ou des colonnes, dans votre jeu de résultats.  
  
 Si vous le souhaitez, votre **commande** classe peut implémenter <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>. Cette interface permet à une classe d'implémentation d'analyser une requête et de retourner une liste de paramètres dans la requête. Les fonctionnalités de l'interface <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> sont uniquement utilisées dans le Concepteur de rapports. Lorsque vous implémentez <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>, vous permettez aux utilisateurs du Concepteur de rapports d'être invité à fournir des paramètres dès qu'un rapport est exécuté en mode Aperçu. En outre, vous pouvez afficher les paramètres dans le **paramètres** onglet de la **jeu de données** boîte de dialogue.  
  
> [!NOTE]  
>  Vous ne devez pas implémenter <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> si votre extension personnalisée pour le traitement des données ne prend en charge aucun paramètre.  
  
 Pour obtenir un exemple **commande** implémentation de la classe, consultez [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implémentation d’une Extension de traitement des données](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Bibliothèque d’Extension de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
