---
title: Gestionnaire de connexions du Stockage Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpstorageconn.f1
- sql11.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ea689f96911af35176d6467e73d496b59f35e3c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62833557"
---
# <a name="azure-storage-connection-manager"></a>Gestionnaire de connexions Azure Storage
  Le Gestionnaire de connexions Azure Storage permet à un package SSIS (SQL Server Integration Services) de se connecter à un compte Azure Storage en utilisant les valeurs que vous spécifiez pour les propriétés Nom du compte de stockage et Clé de compte.  
  
1.  Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS** , sélectionnez **AzureStorage**, puis cliquez sur **Ajouter**.  
  
2.  Dans la boîte de dialogue Éditeur du gestionnaire de connexions du Stockage Azure, choisissez **Utiliser un compte Azure** pour vous connecter à un service de gestion de données Azure par Internet, ou choisissez **Utiliser le compte de développeur local** pour vous connecter au service local hébergé par l’émulateur de Stockage Azure.  
  
3.  Si vous avez sélectionné l’option **Utiliser un compte Azure** , procédez comme suit :  
  
    1.  Renseignez les champs **Nom du compte de stockage** et **Clé de compte**. Ces valeurs seront stockées en tant que données sensibles dans le package SSIS.  
  
    2.  Sélectionnez **Utiliser HTTPS** si vous souhaitez utiliser HTTPS plutôt que HTTP pour vous connecter au service de gestion de données Azure.  
  
4.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
5.  Les propriétés du gestionnaire de connexions que vous avez créées apparaissent dans la fenêtre **Propriétés** .  
  
  
