---
title: Gestionnaire de connexions du Stockage Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 25338d4e05ab8c6cb7a4008230a340dc339e9bbd
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2018
ms.locfileid: "35409951"
---
# <a name="azure-storage-connection-manager"></a>Gestionnaire de connexions Azure Storage
  Le **Gestionnaire de connexions Azure Storage** permet à un package SSIS (SQL Server Integration Services) de se connecter à un compte Azure Storage en utilisant les valeurs que vous spécifiez pour les propriétés Nom du compte de stockage et Clé de compte.  
   
 Le **gestionnaire de connexions du stockage Azure** est un composant de [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md). 
  
1.  Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS** , sélectionnez **AzureStorage**, puis cliquez sur **Ajouter**.  
  
2.  Dans la boîte de dialogue Éditeur du gestionnaire de connexions Azure Storage, choisissez **Utiliser un compte Azure** pour vous connecter à un service de gestion de données Azure par Internet, ou choisissez **Utiliser le compte de développeur local** pour vous connecter au service local hébergé par l’émulateur de stockage Azure.  
  
3.  Si vous avez sélectionné l’option **Utiliser un compte Azure** , procédez comme suit :  
  
    1.  Renseignez les champs **Nom du compte de stockage** et **Clé de compte** . Ces valeurs seront stockées en tant que données sensibles dans le package SSIS.  
  
    2.  Sélectionnez **Utiliser HTTPS** si vous souhaitez utiliser HTTPS plutôt que HTTP pour vous connecter au service de gestion de données Azure.  
  
4.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
5.  Les propriétés du gestionnaire de connexions que vous avez créées apparaissent dans la fenêtre **Propriétés** .  
  
  
