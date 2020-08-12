---
title: Mise en œuvre d’une classe de commande pour une extension pour le traitement des données | Microsoft Docs
description: Découvrez comment implémenter une classe de commande pour une extension pour le traitement des données afin que l’extension puisse formuler des requêtes et les transmettre à la source de données.
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7150b14354be738baa8a127cfe7025dc3245b03e
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529518"
---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a>Implémentation d'une classe Command pour une extension pour le traitement des données
  L’objet **Command** formule une demande et la passe à la source de données. Le texte de la commande peut prendre de nombreuses formes syntaxiques, notamment texte et XML. Si des résultats sont retournés, l’objet **Command** les retourne sous la forme d’un objet **DataReader**.  
  
 Pour créer une classe **Command**, implémentez <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>. Implémentez la méthode <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> pour retourner un jeu de résultats sous la forme d’un objet **DataReader**. La méthode <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> de votre classe **Command** doit inclure une implémentation qui utilise une énumération <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> comme argument. Si vous déployez votre extension pour le traitement des données sur le Concepteur de rapports, vous devez inclure une implémentation qui gère un cas <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> dans la méthode <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>. Une implémentation de type schéma uniquement est utilisée pour fournir une liste de champs au Concepteur de rapports. L’objet **DataReader** retourné par la méthode <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> doit contenir des informations de nom et de type pour les champs ou les colonnes de votre jeu de résultats.  
  
 Si vous le souhaitez, votre classe **Command** peut également implémenter <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>. Cette interface permet à une classe d'implémentation d'analyser une requête et de retourner une liste de paramètres dans la requête. Les fonctionnalités de l'interface <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> sont uniquement utilisées dans le Concepteur de rapports. Lorsque vous implémentez <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>, vous permettez aux utilisateurs du Concepteur de rapports d'être invité à fournir des paramètres dès qu'un rapport est exécuté en mode Aperçu. De plus, vous pouvez consulter les paramètres sous l’onglet **Paramètres** de la boîte de dialogue **Jeu de données**.  
  
> [!NOTE]  
>  Vous ne devez pas implémenter <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> si votre extension personnalisée pour le traitement des données ne prend en charge aucun paramètre.  
  
 Pour un exemple d’implémentation de la classe **Command**, consultez [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (Exemples Reporting Services pour le produit SQL Server).  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implémentation d’une extension pour le traitement des données](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Bibliothèque d'extensions Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
