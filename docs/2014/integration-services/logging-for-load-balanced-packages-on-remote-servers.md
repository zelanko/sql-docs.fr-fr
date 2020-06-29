---
title: Journalisation des packages à charge équilibrée sur les serveurs distants | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], remote packages
ms.assetid: fd571567-b625-4f9a-8b7e-42c5c588b11b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b45fa6607d6edc1559d8ebcbbbc7598e11eac408
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440286"
---
# <a name="logging-for-load-balanced-packages-on-remote-servers"></a>Journalisation des packages à charge équilibrée sur les serveurs distants
  Il est plus facile pour un administrateur de gérer les journaux de tous les packages enfants en cours d'exécution sur différents serveurs lorsque tous ces packages enfants utilisent le même module fournisseur d'informations et qu'ils écrivent tous dans la même destination. Une manière de créer un fichier journal commun pour tous les packages enfants est de configurer les packages enfants de telle sorte qu'ils inscrivent leurs événements dans un module fournisseur d'informations SQL Server. Vous pouvez configurer tous les packages pour qu'ils utilisent la même base de données, le même serveur et la même instance du serveur.  
  
 Pour afficher les fichiers journaux, l'administrateur n'a à se connecter qu'à un seul serveur pour afficher les fichiers journaux de tous les packages enfants.  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la façon d’activer la journalisation dans un package, consultez [Activer la journalisation des packages dans SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  
