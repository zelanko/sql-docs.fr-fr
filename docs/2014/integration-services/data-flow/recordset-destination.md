---
title: Destination du recordset | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.recordsetdest.f1
helpviewer_keywords:
- Recordset destination
- ADO recordsets [Integration Services]
- destinations [Integration Services], Recordset
- in-memory ADO recordsets [Integration Services]
ms.assetid: be973cf1-c4ff-49f8-987e-314c08ef98e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1acc29c904e9020721e8ac62dff09a8ec29a392
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85431486"
---
# <a name="recordset-destination"></a>Destination de l'ensemble d'enregistrements
  La destination de l'ensemble d'enregistrements crée et remplit un ensemble d'enregistrements ADO en mémoire. La forme de l'ensemble d'enregistrements est définie par l'entrée de la destination d'ensemble d'enregistrements au moment de la conception.  
  
## <a name="configuration-of-the-recordset-destination"></a>Configuration de la destination de l'ensemble d'enregistrements  
 Pour configurer la destination de l'ensemble d'enregistrements,vous devez spécifier la variable qui contient l'ensemble d'enregistrements ADO.  
  
 Au moment de l’exécution, un ensemble d’enregistrements ADO est écrit dans la variable du type, Object, qui est spécifié dans la propriété VariableName de la destination de l’ensemble d’enregistrements. La variable rend ensuite l'ensemble d'enregistrements disponible en dehors du flux de données, où il peut être utilisé par des scripts et d'autres éléments de package.  
  
 Cette source possède une entrée. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../common-properties.md)  
  
-   [Propriétés personnalisées de la destination du jeu d’enregistrements](recordset-destination-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-tasks"></a>Tâches associées  
 [Utiliser une destination de jeu d’enregistrements](recordset-destination.md)  
  
  
