---
title: Éditeur du Gestionnaire de connexions Excel | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.excelconnection.f1
helpviewer_keywords:
- Excel Connection Manager Editor
ms.assetid: 7ff097e4-cafb-4885-a898-05b2a46628c1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 22ea5f2f087949718e5dbfc8702756e008ee721e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62769815"
---
# <a name="excel-connection-manager-editor"></a>Éditeur du gestionnaire de connexions Excel
  La boîte de dialogue **Éditeur du gestionnaire de connexions Excel** vous permet d'ajouter une connexion à un classeur [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] existant ou nouveau.  
  
 Pour en savoir plus sur le gestionnaire de connexions Excel, consultez [Excel Connection Manager](connection-manager/excel-connection-manager.md).  
  
> [!NOTE]  
>  Vous ne pouvez pas vous connecter à un fichier Excel protégé par mot de passe.  
  
## <a name="options"></a>Options  
 **Chemin de fichier Excel**  
 Tapez le chemin d'accès et le nom du fichier d'un classeur Excel (.xls) existant ou nouveau.  
  
> [!WARNING]  
>  Le **éditeur de Destination Excel** crée automatiquement le fichier Excel lorsque vous sélectionnez un **connexion Excel** que pointe vers un nouveau ou non-existant de fichiers, puis **New** pour **Nom de la feuille Excel**.  
  
 **Parcourir**  
 Utilisez la boîte de dialogue **Ouvrir** pour rechercher le dossier dans lequel le fichier Excel se trouve ou accéder à l’emplacement où vous souhaitez créer le fichier.  
  
 **Version Excel**  
 Spécifiez la version de Microsoft Excel qui a été utilisée pour créer le fichier.  
  
|Option|Description|  
|------------|-----------------|  
|Excel 97-2003|Le fichier a été créé à l'aide d'Excel 97 ou version ultérieure.|  
|Excel 3.0|Fichier a été créé à l’aide d’Excel 3.0.|  
|Excel 4.0|Le fichier a été créé à l'aide d'Excel 4.0.|  
|Excel 5.0|Le fichier a été créé à l'aide d'Excel 95 (7.0).|  
  
 **La première ligne possède des noms de colonnes**  
 Permet de spécifier si la première ligne de données dans la feuille de calcul sélectionnée contient les noms des colonnes. La valeur par défaut de cette option est **True**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](control-flow/foreach-loop-container.md)  
  
  
