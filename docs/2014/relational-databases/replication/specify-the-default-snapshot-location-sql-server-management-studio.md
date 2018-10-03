---
title: Spécifier l’emplacement par défaut des instantanés (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], default locations
- default snapshot locations
ms.assetid: 27c5d9ad-a915-4c59-a8b7-82e3af61ac4d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fc9734cb3da7c61da7c15ce108cd86f09be8ea1b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48148839"
---
# <a name="specify-the-default-snapshot-location-sql-server-management-studio"></a>Spécifier l'emplacement par défaut des instantanés (SQL Server Management Studio)
  Spécifiez l'emplacement par défaut des instantanés dans la page **Dossier d'instantanés** de l'Assistant Configuration de la distribution. Pour plus d’informations sur l’utilisation de cet Assistant, consultez [Configurer la publication et la distribution](configure-publishing-and-distribution.md). Si vous créez une publication sur un serveur qui n'est pas configuré en tant que serveur de distribution, spécifiez un emplacement d'instantanés par défaut dans la page **Dossier d'instantanés** de l'Assistant Nouvelle publication. Pour plus d’informations sur l’utilisation de cet Assistant, consultez [Créer une publication](publish/create-a-publication.md).  
  
 Modifiez l’emplacement par défaut des instantanés dans la page **Serveurs de publication** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveur de distribution>**. Pour plus d’informations, consultez [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md). Définissez le dossier d’instantanés pour chaque publication dans la boîte de dialogue **Propriétés de publication - \<Publication>**. Pour plus d'informations, voir [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  
  
### <a name="to-modify-the-default-snapshot-location"></a>Pour modifier l'emplacement par défaut des instantanés  
  
1.  Dans la page **Serveurs de publication** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveur de distribution>**, cliquez sur le bouton des propriétés (**…**) du serveur de publication pour lequel vous voulez modifier l’emplacement par défaut des instantanés.  
  
2.  Dans la boîte de dialogue **Propriétés du serveur de publication - \<Serveur de publication>**, entrez une valeur pour la propriété **Dossier des captures instantanées par défaut**.  
  
    > [!NOTE]  
    >  L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si vous utilisez des abonnements par extraction, vous devez spécifier un répertoire partagé en tant que chemin UNC, par exemple \\\nom_ordinateur\snapshot. Pour plus d’informations, consultez [Sécuriser le dossier d’instantanés](security/secure-the-snapshot-folder.md).  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Autres emplacements du dossier d’instantanés](alternate-snapshot-folder-locations.md)   
 [Initialiser un abonnement avec un instantané](initialize-a-subscription-with-a-snapshot.md)  
  
  
