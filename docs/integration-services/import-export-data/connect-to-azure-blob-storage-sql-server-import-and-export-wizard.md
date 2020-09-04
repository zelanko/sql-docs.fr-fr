---
description: Se connecter à Stockage Blob Azure (Assistant Importation et Exportation SQL Server)
title: Se connecter à Stockage Blob Azure (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 02/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e2e482b8-5f90-48c5-93fb-b412ed52659f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9848ba94687f6f4555492de868f32431b3e1de84
ms.sourcegitcommit: 9be0047805ff14e26710cfbc6e10d6d6809e8b2c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "89042392"
---
# <a name="connect-to-azure-blob-storage-sql-server-import-and-export-wizard"></a>Se connecter à Stockage Blob Azure (Assistant Importation et Exportation SQL Server)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


Cette rubrique vous montre comment se connecter à une source de données **Stockage Blob Azure** à partir de la page **Choisir une source de données** ou **Choisir une destination** de l’Assistant Importation et Exportation SQL Server.

> [!NOTE]
> Pour utiliser la source ou la destination des objets blob Azure, vous devez installer le Feature Pack Azure pour SQL Server Integration Services.
> - Pour télécharger le Feature Pack, consultez [Microsoft SQL Server 2016 Integration Services Feature Pack pour Azure](https://www.microsoft.com/download/details.aspx?id=49492).
> 
> - Pour plus d’informations, consultez [Feature Pack Azure pour Integration Services &#40;SSIS&#41;](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

La capture d’écran suivante présente les options de configuration d’une connexion à Stockage Blob Azure.

![Connexion à Azure Blob Storage](../../integration-services/import-export-data/media/azure-blob-storage-connection.png)

## <a name="options-to-specify"></a>Options à spécifier

> [!NOTE]
> Les options de connexion de ce fournisseur de données sont les mêmes, que Stockage Blob Azure soit la source ou la destination. Autrement dit, les options que vous voyez sont identiques dans les pages **Choisir une source de données** et **Choisir une destination** de l’Assistant.

 **Utiliser un compte Azure**  
 Indiquez si vous souhaitez utiliser un compte en ligne.
  
 **Nom du compte de stockage**  
 Entrez le nom du compte de stockage Azure.  
  
**Clé de compte**  
Entrez la clé du compte de stockage Azure.  
  
 **Utiliser le protocole HTTPS**  
 Indiquez si vous souhaitez vous connecter au compte de stockage avec HTTP ou HTTPS.  
  
 **Utiliser le compte de développeur local**  
 Spécifiez s’il convient d’utiliser l’émulateur de stockage Azure sur l’ordinateur local.  
  
 **Nom du conteneur d’objets blob**  
 Sélectionnez un nom dans la liste des conteneurs de stockage disponibles dans le compte de stockage spécifié.  
  
 **Format du fichier d’objets blob**  
 Sélectionnez le format de fichier Texte ou Avro.  
  
 **Caractère séparateur de colonnes**  
 Si vous avez sélectionné le format Texte, entrez le caractère délimiteur de colonne.  
  
 **Utiliser la première ligne comme noms des colonnes**  
 Spécifiez si la première ligne de données contient des noms de colonne.  

## <a name="see-also"></a>Voir aussi
[Choisir une source de données](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[Choisir une destination](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)

