---
description: destination DataReader
title: Destination DataReader | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.datareaderdest.f1
helpviewer_keywords:
- DataReader destination
- destinations [Integration Services], DataReader
ms.assetid: 56fcc4bf-c901-42c3-a71d-110039293431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: efae870a84f4009664d82faa5bf8c8015562f56a
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92194198"
---
# <a name="datareader-destination"></a>destination DataReader

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  La destination DataReader expose les données d’un flux à l’aide de l’interface **DataReader** ADO.NET. Les données peuvent ensuite être utilisées par d'autres applications. Vous pouvez par exemple configurer la source de données d’un rapport [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de sorte qu’elle utilise le résultat d’exécution d’un package [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Pour ce faire, vous devez créer un flux qui implémente la destination DataReader.  
  
 Pour plus d’informations sur l’accès aux valeurs de la destination DataReader et sur leur lecture par programmation, consultez [Chargement de la sortie d’un package local](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md).  
  
## <a name="configuration-of-the-datareader-destination"></a>Configuration de la destination DataReader  
 Vous pouvez spécifier une valeur de délai d'attente de la destination DataReader et indiquer si la destination doit échouer en cas de dépassement de délai. Un délai d'attente est dépassé si l'application ne demande aucune donnée dans le délai spécifié.  
  
 La destination DataReader possède une entrée. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](./set-the-properties-of-a-data-flow-component.md)  
  
-   [Propriétés personnalisées de la destination DataReader](../../integration-services/data-flow/datareader-destination-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir les propriétés, consultez [Définir les propriétés d’un composant de flux de données](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
