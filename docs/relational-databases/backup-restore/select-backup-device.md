---
title: Sélectionner l’unité de sauvegarde | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql13.swb.selectbackupdevice.f1
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 77e9a3bc2e9460981f06ed3ffb3c1d95e352b3f0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62516209"
---
# <a name="select-backup-device"></a>Sélectionner l'unité de sauvegarde
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La boîte de dialogue **Sélectionner l'unité de sauvegarde** vous permet de sélectionner une unité logique de sauvegarde pour l'opération de restauration.  
  
 Une unité logique de sauvegarde est une unité logique définie par l'utilisateur et qui correspond à une unité physique, telle qu'un lecteur de bande ou un lecteur de disque, et fournie par le système d'exploitation.  
  
> [!NOTE]  
>  Si une sauvegarde utilise plusieurs unités de sauvegarde, elles doivent toutes correspondre à un même type d'unité.  
  
 **Pour utiliser SQL Server Management Studio pour afficher le contenu d'une unité de sauvegarde**  
  
-   [Afficher le contenu d’un fichier ou d’une bande de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>Options  
 **unité de sauvegarde**  
 Dans la zone de liste, sélectionnez le nom de l'unité logique de sauvegarde à partir de laquelle vous voulez effectuer la restauration.  
  
 Pour plus d’informations sur la façon d’afficher le contenu d’une unité de sauvegarde, consultez [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md).  
  
## <a name="remarks"></a>Notes   
 Si aucune unité logique de sauvegarde ne contient la sauvegarde recherchée dans la liste, il est possible que la sauvegarde ait été écrite directement sur un ou plusieurs fichiers ou lecteurs de bande. Le cas échant, fermez la boîte de dialogue **Sélectionner l'unité de sauvegarde** et dans la boîte de dialogue **Spécifier la sauvegarde** , sélectionnez **Fichier** ou **Bande** dans la zone de liste **Support de sauvegarde** .  
  
## <a name="see-also"></a> Voir aussi  
 [Unités de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
  
