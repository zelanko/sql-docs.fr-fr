---
title: Sélectionner l’unité de sauvegarde | Microsoft Docs
description: Pour les restaurations SQL Server, la boîte de dialogue Sélectionner l’unité de sauvegarde vous permet de sélectionner une unité logique de sauvegarde pour l’opération de restauration.
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
author: cawrites
ms.author: chadam
ms.openlocfilehash: 3eb2dc44dde731d77ecea441532d45f8b7fa8b39
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2020
ms.locfileid: "96125497"
---
# <a name="select-backup-device"></a>Sélectionner l'unité de sauvegarde
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
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
  
  
