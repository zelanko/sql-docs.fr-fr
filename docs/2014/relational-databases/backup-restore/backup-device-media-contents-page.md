---
title: Unité de sauvegarde (page Contenu du support) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdevice.contents.f1
ms.assetid: 5fc7bd22-b6d8-4af1-8a58-2e7d0b994d08
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 524e6d8e5ec987a20d693cb1f7e06b30bc27c0b5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130494"
---
# <a name="backup-device-media-contents-page"></a>Unité de sauvegarde (page Contenu du support)
  La boîte de dialogue **Unité de sauvegarde** vous permet  d'afficher les informations de sauvegarde. Ces informations décrivent le périphérique, le support, le jeu de supports, ainsi que le ou les jeux de sauvegarde.  
  
 **Pour utiliser SQL Server Management Studio pour afficher le contenu d'une unité de sauvegarde**  
  
-   [Afficher le contenu d’un fichier ou d’une bande de sauvegarde &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>Options  
 Affichez des informations sur le support individuel, le support de sauvegarde et les jeux de sauvegarde.  
  
 **Support**  
 Disque ou jeu de bandes sur lequel sont stockées les informations de sauvegarde.  
  
 **Séquence du support**  
 Répertorie le numéro de séquence du support, le numéro de séquence de la famille et, le cas échéant, l'identificateur du support miroir. Chaque support de sauvegarde physique est associé à un numéro de séquence de support indiquant l'ordre d'utilisation des supports. Le support de sauvegarde initial est référencé par le chiffre 1, le deuxième support (la première bande de continuation) par le chiffre 2 et ainsi de suite. Lorsque le jeu de sauvegarde est restauré, ces numéros de séquence de support garantissent que l'opérateur qui effectue la restauration monte le support approprié dans l'ordre correct.  
  
 **Créé le**  
 Indique la date et l'heure de création du support de sauvegarde.  
  
 **Support de sauvegarde**  
 Un support de sauvegarde est une collection ordonnée de supports de sauvegarde dans laquelle une ou plusieurs opérations de sauvegarde ont écrit en utilisant un nombre constant d'unités de sauvegarde.  
  
 **Nom**  
 Indique le nom du support de sauvegarde, s'il existe.  
  
 **Description**  
 Indique la description du support de sauvegarde, s'il existe.  
  
 **Nombre de familles de supports**  
 Indique le nombre de familles dans le support de sauvegarde. Chaque support de sauvegarde est une collection comprenant une ou plusieurs familles de supports. Toutes les opérations effectuées sur une unité de sauvegarde donnée (ou sur un groupe d'unités de sauvegarde miroir) constituent une seule famille de supports. Chaque support de sauvegarde contient une famille de supports par unité distincte (ou groupe d'unités en miroir) ; par exemple, si un support de sauvegarde utilise deux unités de sauvegarde non mises en miroir, il contient deux familles de supports.  
  
 **Jeux de sauvegarde**  
 Affiche les informations relatives au(x) jeu(x) de sauvegarde contenus dans les supports. Un jeu de sauvegarde est le résultat d'une opération de sauvegarde réussie, dont le contenu est distribué entre les supports d'un ensemble d'unités de sauvegarde.  
  
|En-tête|Valeurs|  
|------------|------------|  
|**Nom**|Nom du jeu de sauvegarde.|  
|**Type**|Objet sauvegardé : Base de données, Fichier ou *\<vide>* (pour les journaux des transactions).|  
|**Composant**|Type de sauvegarde effectué : Complète, Différentielle ou Journal des transactions.|  
|**Server**|Nom de l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui a effectué l'opération de sauvegarde.|  
|**Sauvegarde de la base de données**|Le nom de la base de données qui a été sauvegardée.|  
|**Position**|La position du jeu de sauvegarde dans le volume.|  
|**Date**|Date et heure de fin de l'opération de sauvegarde, exprimée d'après les paramètres régionaux du client.|  
|**Taille**|Taille du jeu de sauvegarde, exprimée en octets.|  
|**Nom d'utilisateur**|Nom de l'utilisateur qui a exécuté l'opération de sauvegarde.|  
|**Expiration**|La date et l'heure d'expiration du jeu de sauvegarde.|  
  
##  <a name="RelatedTasks"></a> Tâches associées  
  
-   [Définir une unité de sauvegarde logique pour un fichier de disque &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)  
  
-   [Définir une unité de sauvegarde logique pour un lecteur de bande &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
-   [Spécifier un disque ou une bande comme destination de sauvegarde &#40;SQL Server&#41;](specify-a-disk-or-tape-as-a-backup-destination-sql-server.md)  
  
-   [Supprimer une unité de sauvegarde &#40;SQL Server&#41;](delete-a-backup-device-sql-server.md)  
  
-   [Définir la date d’expiration d’une sauvegarde &#40;SQL Server&#41;](set-the-expiration-date-on-a-backup-sql-server.md)  
  
-   [Afficher le contenu d’un fichier ou d’une bande de sauvegarde &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Afficher les fichiers de données et les fichiers journaux dans un jeu de sauvegarde &#40;SQL Server&#41;](view-the-data-and-log-files-in-a-backup-set-sql-server.md)  
  
-   [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
-   [Restaurer une sauvegarde à partir d’une unité &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Unités de sauvegarde &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
