---
title: Script de déploiement d’instance CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5b8f895fb591d8cf909632aeab4e48d31bbcb343
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37173140"
---
# <a name="cdc-instance-deployment-script"></a>Script de déploiement d'instance CDC
  Boîte de dialogue de script de déploiement d'instance de capture de données modifiées qui affiche le script de déploiement d'instance de capture de données modifiées. Ce script peut être utilisé pour recréer la base de données CDC avec tous ses artefacts sur une autre instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 À la fin du script de déploiement, vous devez vous assurer de ce qui suit :  
  
-   Le script de déploiement suppose que l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible a été préparée pour la capture de données modifiées Oracle, à l'aide de la console de configuration du service de capture de données modifiées Oracle ou à l'aide du **script de préparation** créé par le programme.  
  
-   La partie du script utilisée pour activer la base de données pour la capture de données modifiées doit être exécutée par un `sysadmin`.  
  
-   Le script ne conserve pas le mot de passe d'exploration de données de journaux Oracle. Il doit être défini manuellement une fois le script exécuté et le service de capture de données modifiées Oracle démarré.  
  
 Sélectionnez les options suivantes dans la boîte de dialogue **Script de déploiement d'instance CDC** .  
  
 **Enregistrer sous**  
 Enregistre le script dans un fichier texte que vous pouvez enregistrer dans n'importe quel emplacement de votre choix. Vous pouvez copier le fichier script vers tout autre serveur en vue de l'exécuter.  
  
 **Copier**  
 Copie le script dans le Presse-papiers. Vous pouvez ensuite coller le script dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou dans un éditeur de texte pour exécuter des scripts ultérieurement.  
  
## <a name="see-also"></a>Voir aussi  
 [Préparer SQL Server pour CDC](prepare-sql-server-for-cdc.md)  
  
  
