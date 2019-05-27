---
title: Équilibrage de la journalisation des Packages sur des serveurs distants | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], remote packages
ms.assetid: fd571567-b625-4f9a-8b7e-42c5c588b11b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 64dec3a89b883d6b3234f65896bb89d3bfde5305
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66057850"
---
# <a name="logging-for-load-balanced-packages-on-remote-servers"></a>Journalisation des packages à charge équilibrée sur les serveurs distants
  Il est plus facile pour un administrateur de gérer les journaux de tous les packages enfants en cours d'exécution sur différents serveurs lorsque tous ces packages enfants utilisent le même module fournisseur d'informations et qu'ils écrivent tous dans la même destination. Une manière de créer un fichier journal commun pour tous les packages enfants est de configurer les packages enfants de telle sorte qu'ils inscrivent leurs événements dans un module fournisseur d'informations SQL Server. Vous pouvez configurer tous les packages pour qu'ils utilisent la même base de données, le même serveur et la même instance du serveur.  
  
 Pour afficher les fichiers journaux, l'administrateur n'a à se connecter qu'à un seul serveur pour afficher les fichiers journaux de tous les packages enfants.  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la façon d’activer la journalisation dans un package, consultez [Activer la journalisation des packages dans SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  
