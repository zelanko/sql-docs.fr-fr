---
title: Sélectionner l’unité de sauvegarde | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.selectbackupdevice.f1
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6135239b182c66ae4622dcf9af704fb30f167f6f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044515"
---
# <a name="select-backup-device"></a>Sélectionner l'unité de sauvegarde
  La boîte de dialogue **Sélectionner l'unité de sauvegarde** vous permet de sélectionner une unité logique de sauvegarde pour l'opération de restauration.  
  
 Une unité logique de sauvegarde est une unité logique définie par l'utilisateur et qui correspond à une unité physique, telle qu'un lecteur de bande ou un lecteur de disque, et fournie par le système d'exploitation.  
  
> [!NOTE]  
>  Si une sauvegarde utilise plusieurs unités de sauvegarde, elles doivent toutes correspondre à un même type d'unité.  
  
 **Pour utiliser SQL Server Management Studio pour afficher le contenu d'une unité de sauvegarde**  
  
-   [Afficher le contenu d’un fichier ou d’une bande de sauvegarde &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>Options  
 **unité de sauvegarde**  
 Dans la zone de liste, sélectionnez le nom de l'unité logique de sauvegarde à partir de laquelle vous voulez effectuer la restauration.  
  
 Pour plus d’informations sur la façon d’afficher le contenu d’une unité de sauvegarde, consultez [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md).  
  
## <a name="remarks"></a>Notes  
 Si aucune unité logique de sauvegarde ne contient la sauvegarde recherchée dans la liste, il est possible que la sauvegarde ait été écrite directement sur un ou plusieurs fichiers ou lecteurs de bande. Le cas échant, fermez la boîte de dialogue **Sélectionner l'unité de sauvegarde** et dans la boîte de dialogue **Spécifier la sauvegarde** , sélectionnez **Fichier** ou **Bande** dans la zone de liste **Support de sauvegarde** .  
  
## <a name="see-also"></a>Voir aussi  
 [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md)  
  
  