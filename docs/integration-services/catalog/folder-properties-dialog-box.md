---
title: Boîte de dialogue Propriétés du dossier | Microsoft Docs
ms.custom: ''
ms.date: 08/26/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.ssms.isfolderprop.permissions.f1
- sql13.ssis.ssms.iscreatefolder.f1
- sql13.ssis.ssms.isfolderprop.general.f1
ms.assetid: d9a2bfae-fcc8-46be-b588-4a9db03f7e45
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19f23e57fdb77a88ecf7c7b531c9c837e2c740ce
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71299000"
---
# <a name="folder-properties-dialog-box"></a>Propriétés du dossier, boîte de dialogue

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Un dossier contient des projets et des environnements dans le catalogue **SSISDB** . Chaque dossier définit des autorisations qui s'appliquent au contenu du dossier. Pour plus d’informations sur les autorisations [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , consultez [catalog.grant_permission &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database.md).  
  
## <a name="to-set-folder-description-and-permissions"></a>Pour définir la description et les autorisations d'un dossier  
  
1.  Cliquez avec le bouton droit sur le dossier et sélectionnez **Propriétés**.  
  
2.  Dans la page **Général** , sélectionnez **Description** sous **Général** , puis entrez une description facultative.  
  
3.  Dans la page **Autorisations** , cliquez sur **Parcourir**, sélectionnez un ou plusieurs principaux de base de données, puis cliquez sur **OK**.  
  
4.  Sélectionnez un nom sous **Connexions ou rôles** et spécifiez les autorisations appropriées sous **Autorisations**.  
  
5.  Cliquez sur **OK** pour accepter les modifications et fermer la boîte de dialogue **Propriétés du dossier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Serveur Integration Services &#40;SSIS&#41;](../integration-services-ssis-packages.md)   
 [catalog.grant_permission &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database.md)  
  
  
