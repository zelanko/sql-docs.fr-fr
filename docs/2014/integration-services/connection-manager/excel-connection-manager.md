---
title: Gestionnaire de connexions Excel | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 432d48bbe848d6f66e9f3dae5365abe10d8deb62
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62833842"
---
# <a name="excel-connection-manager"></a>Gestionnaire de connexions Excel
  Un gestionnaire de connexions Excel permet à un package de se connecter à un fichier [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel. La source Excel et la destination Excel qui [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] incluent utilisent le gestionnaire de connexions Excel.  
  
 Lorsque vous ajoutez un gestionnaire de connexions Excel à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera converti en connexion Excel au moment de l'exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection `Connections` du package.  
  
 La propriété `ConnectionManagerType` du gestionnaire de connexions a pour valeur `EXCEL`.  
  
> [!NOTE]  
>  Vous ne pouvez pas vous connecter à un fichier Excel protégé par mot de passe.  
  
## <a name="configuration-of-the-excel-connection-manager"></a>Configuration du gestionnaire de connexions Excel  
 Vous pouvez configurer le gestionnaire de connexions Excel de plusieurs manières :  
  
-   Spécifiez le chemin d'accès du fichier Excel.  
  
-   Spécifiez la version d'Excel utilisée pour créer le fichier.  
  
-   Indiquez si la première ligne des données qui ont fait l'objet d'un accès dans les feuilles de calcul ou les plages sélectionnées contient les noms de colonnes.  
  
 Si le gestionnaire de connexions Excel est utilisé par une source Excel, les noms de colonnes sont inclus avec les données extraites. S'il est utilisé par une destination Excel, les noms de colonnes sont inclus dans les données écrites.  
  
 Le gestionnaire de connexions Excel utilise le fournisseur [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB pour Jet 4.0 et son pilote de prise en charge Excel ISAM (Indexed Sequential Access Method) pour se connecter aux sources de données Excel, puis y lire et écrire des données. Pour plus d’informations sur le comportement de ce fournisseur et de ce pilote lorsqu’il est utilisé avec des sources Excel et des destinations Excel, consultez [source](../data-flow/excel-source.md) Excel et [destination](../data-flow/excel-destination.md)Excel.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Éditeur du gestionnaire de connexions Excel](../excel-connection-manager-editor.md).  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
 Pour plus d’informations sur le bouclage dans un groupe de fichiers Excel, consultez [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../control-flow/foreach-loop-container.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Effectuer une boucle dans des fichiers et des tables Excel en utilisant un conteneur de boucles Foreach](../control-flow/foreach-loop-container.md)  
  
-   [Importer des données à partir d’Excel ou exporter des données vers Excel avec SQL Server Integration Services (SSIS)](../load-data-to-from-excel-with-ssis.md)
  
  
