---
title: Gestionnaire de connexions du Stockage Azure | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 8a115dafb386323bc1f4738720e7576657d22543
ms.sourcegitcommit: 2efb0fa21ff8093384c1df21f0e8910db15ef931
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2019
ms.locfileid: "68316687"
---
# <a name="azure-storage-connection-manager"></a>Gestionnaire de connexions Azure Storage

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

  **Azure Storage Connection Manager** permet à un package SSIS de se connecter à un compte Stockage Azure.
   
 Le **gestionnaire de connexions du stockage Azure** est un composant de [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md). 
  
Dans la boîte de dialogue **Ajout d’un gestionnaire de connexions SSIS** , sélectionnez **AzureStorage**, puis cliquez sur **Ajouter**.  
  
Les propriétés suivantes sont disponibles.

- **Service :** spécifie le service de stockage auquel se connecter.
- **Account name (Nom du compte) :** spécifie le nom du compte de stockage.
- **Authentication (Authentification) :** spécifie la méthode d’authentification à utiliser. Les authentifications **AccessKey** et **ServicePrincipal** sont prises en charge.
    - **AccessKey :** pour cette méthode d’authentification, spécifiez la **clé de compte**.
    - **ServicePrincipal :** pour cette méthode d’authentification, spécifiez l’**ID d’application**, la **clé d’application** et l’**ID de locataire** du principal du service.
      Pour que la **connexion de test** fonctionne, le principal de service doit disposer au moins du rôle **Lecteur des données Blob du stockage** pour le compte de stockage.
      Pour plus d’informations, consultez [cette page](https://docs.microsoft.com/azure/storage/common/storage-auth-aad-rbac-portal#assign-rbac-roles-using-the-azure-portal).
- **Environment :** spécifie l’environnement de cloud qui héberge le compte de stockage.
