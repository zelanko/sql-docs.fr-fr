---
title: Équilibrage de la journalisation des Packages sur des serveurs à distance | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- logs [Integration Services], remote packages
ms.assetid: fd571567-b625-4f9a-8b7e-42c5c588b11b
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 85f423c0d8b194a73042e808326d3ce28ef1de0d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051300"
---
# <a name="logging-for-load-balanced-packages-on-remote-servers"></a>Journalisation des packages à charge équilibrée sur les serveurs distants
  Il est plus facile pour un administrateur de gérer les journaux de tous les packages enfants en cours d'exécution sur différents serveurs lorsque tous ces packages enfants utilisent le même module fournisseur d'informations et qu'ils écrivent tous dans la même destination. Une manière de créer un fichier journal commun pour tous les packages enfants est de configurer les packages enfants de telle sorte qu'ils inscrivent leurs événements dans un module fournisseur d'informations SQL Server. Vous pouvez configurer tous les packages pour qu'ils utilisent la même base de données, le même serveur et la même instance du serveur.  
  
 Pour afficher les fichiers journaux, l'administrateur n'a à se connecter qu'à un seul serveur pour afficher les fichiers journaux de tous les packages enfants.  
  
## <a name="related-tasks"></a>Related Tasks  
 Pour plus d’informations sur la façon d’activer la journalisation dans un package, consultez [Activer la journalisation des packages dans SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  