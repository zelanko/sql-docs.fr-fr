---
title: Sauvegarder la clé de chiffrement (SSRS en Mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.backupencryptionkey.F1
ms.assetid: eb8c82be-323b-4d86-ab10-c1bf69a4abe3
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: db573e1a070b110ff0f5224a6d079f3fe7c377ca
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48061689"
---
# <a name="backup-encryption-key-ssrs-native-mode"></a>Sauvegarder la clé de chiffrement (SSRS en mode natif)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise une clé de chiffrement pour sécuriser les données sensibles stockées dans la base de données de serveur de rapports. La possession d'une sauvegarde de cette clé est essentielle pour garantir l'accès continu aux chaînes de connexion et aux informations d'identification chiffrées. Vous devez avoir une copie de sauvegarde de cette clé si vous déplacez la base de données du serveur de rapports vers un autre ordinateur ou si vous modifiez le nom d'utilisateur ou le mot de passe du compte de service Report Server. Ces deux opérations nécessitent la restauration de la clé à partir d'une copie de sauvegarde que vous avez créée précédemment.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif.  
  
 Pour ouvrir la boîte de dialogue clé de chiffrement de sauvegarde, cliquez sur **clés de chiffrement** dans le volet de navigation de la [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, puis cliquez sur **sauvegarde**. Cette boîte de dialogue s’affiche également lorsque vous mettez à jour le compte de service à l’aide de la page compte de Service dans le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. Pour plus d’informations sur la [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, consultez [Gestionnaire de Configuration de Reporting Services &#40;en Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Options  
 **Emplacement du fichier**  
 Spécifiez un nom de fichier et un emplacement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à la clé symétrique. La clé symétrique n'est jamais stockée en texte clair. Vous devez taper un mot de passe pour protéger le fichier.  
  
 **Mot de passe**  
 Entrez un mot de passe qui protège le fichier contre tout accès non autorisé. Seuls les utilisateurs qui connaissent le mot de passe seront en mesure de restaurer la clé verrouillée à l'intérieur du fichier. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applique une stratégie de mot de passe fort. Le mot de passe doit comporter au moins 8 caractères et inclure une combinaison de caractères alphanumériques majuscules et minuscules, ainsi qu'au moins un caractère symbole.  
  
 **Confirmer le mot de passe**  
 Retapez le mot de passe que vous avez entré.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques d’aide F1 Gestionnaire de Configuration de Reporting Services &#40;SSRS en Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Sauvegarder et restaurer les clés de chiffrement Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [Supprimer et recréer des clés de chiffrement &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [Initialiser un serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [Stocker des données chiffrées du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Clés de chiffrement &#40;SSRS en Mode natif&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)  
  
  
