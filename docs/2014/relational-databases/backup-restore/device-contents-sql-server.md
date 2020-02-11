---
title: Contenu de l’unité (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.bnrdevicecontents.f1
ms.assetid: 95e1902e-8c7a-4830-bdf9-1a6aca414a24
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 890a03221888693c1696059ed5d31a9907ea2872
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62876046"
---
# <a name="device-contents-sql-server"></a>Contenu de l'unité (SQL Server)
  Utilisez cette boîte de dialogue pour consulter les informations de sauvegarde. Ces informations décrivent le périphérique, le support, le jeu de supports, ainsi que le ou les jeux de sauvegarde.  
  
 **Pour utiliser SQL Server Management Studio pour afficher le contenu d'une unité de sauvegarde**  
  
-   [Afficher le contenu d’un fichier ou d’une bande de sauvegarde &#40;SQL Server&#41;](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [Afficher les propriétés et le contenu d’une unité de sauvegarde logique &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a>Options  
 **Média**  
 Disque ou jeu de bandes sur lequel sont stockées les informations de sauvegarde.  
  
 **Séquence du support**  
 Répertorie le numéro de séquence du support, le numéro de séquence de la famille et, le cas échéant, l'identificateur du support miroir. Chaque support de sauvegarde physique est associé à un numéro de séquence de support indiquant l'ordre d'utilisation des supports. Le support de sauvegarde initial est référencé par le chiffre 1, le deuxième support (la première bande de continuation) par le chiffre 2 et ainsi de suite. Lors de la restauration du jeu de sauvegarde, les numéros de séquence des supports garantissent que l'opérateur effectuant la restauration monte le bon support dans le bon ordre.  
  
 **Créé le**  
 Affiche la date de création du support.  
  
 **Support de sauvegarde**  
 Un support de sauvegarde est une collection ordonnée de supports de sauvegarde dans lesquels une ou plusieurs opérations de sauvegarde ont effectué des écritures en utilisant un nombre constant d'unités de sauvegarde.  
  
 **Nom**  
 Affiche le nom du support de sauvegarde.  
  
 **Description**  
 Affiche la description du support de sauvegarde.  
  
 **Nombre de familles de supports**  
 Affiche le nombre de familles de supports. Chaque support de sauvegarde est une collection comprenant une ou plusieurs familles de supports. Toutes les opérations effectuées sur une unité de sauvegarde donnée (ou sur un groupe d'unités de sauvegarde miroir) constituent une seule famille de supports. Chaque support de sauvegarde contient une famille de supports par unité de sauvegarde (ou groupe d'unités miroir) ; par exemple, si un support de sauvegarde utilise deux unités de sauvegarde qui n'ont pas été mises en miroir, le support de sauvegarde contient deux familles de supports.  
  
 **Jeux de sauvegarde**  
 Affiche les informations relatives au(x) jeu(x) de sauvegarde contenus dans les supports. Un jeu de sauvegarde est le résultat d'une opération de sauvegarde réussie dont le contenu est divisé entre les supports présents dans le jeu d'unités de sauvegarde.  
  
|En-tête|Valeurs|  
|------------|------------|  
|**Nom**|Nom du jeu de sauvegarde.|  
|**Type**|Type de sauvegarde effectué : Complète, Différentielle ou Journal des transactions.|  
|**Composant**|Composant sauvegardé : Base de données, Fichier ou *\<vide>* (pour les journaux des transactions).|  
|**Serveur**|Nom de l'instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] qui a effectué l'opération de sauvegarde.|  
|**Sauvegarde de la base de données**|Le nom de la base de données qui a été sauvegardée.|  
|**Position**|La position du jeu de sauvegarde dans le volume.|  
|**Date**|Date et heure de fin de l'opération de sauvegarde, exprimée d'après les paramètres régionaux du client.|  
|**Taille**|Taille du jeu de sauvegarde, exprimée en octets.|  
|**Nom d’utilisateur**|Nom de l'utilisateur qui a exécuté l'opération de sauvegarde.|  
|**Expiration**|La date et l'heure d'expiration du jeu de sauvegarde.|  
  
## <a name="see-also"></a>Voir aussi  
 [Jeux de supports, familles de supports et jeux de sauvegarde &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)  
  
  
