---
title: Restaurer la clé de chiffrement (SSRS en Mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.restoreencryptionkey.F1
ms.assetid: 11ce51e5-f5d4-40b6-88d8-9360fb50e66c
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b537f8413ca460d8eb1991bdd71f1a73ac9ceba1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66092517"
---
# <a name="restore-encryption-key-ssrs-native-mode"></a>Restaurer la clé de chiffrement (SSRS en mode natif)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilise une clé de chiffrement pour sécuriser les données sensibles stockées dans la base de données du serveur de rapports. Pour garantir un accès ininterrompu aux données chiffrées, il importe que vous créiez une sauvegarde de la clé de chiffrement au cas où vous devriez la restaurer ultérieurement en raison de modifications dans le compte de service ou dans le cadre d'une migration planifiée. Cette rubrique est une vue d'ensemble de l'utilisation du Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour restaurer des clés.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif.  
  
 Pour restaurer la clé, vous devez avoir enregistré préalablement une copie de sauvegarde de la clé sur un fichier protégé par mot de passe. Pendant la restauration de la clé, le serveur de rapports remplace la clé existante par la clé trouvée dans le fichier protégé par mot de passe. La clé qui est à l'intérieur du fichier doit être identique à celle utilisée pour chiffrer et déchiffrer les données.  
  
 Pour vérifier que vous avez restauré une clé valide, utilisez le Gestionnaire de rapports pour consulter les abonnements ou un rapport ayant une source de données qui utilise des informations d'identification stockées. Si vous recevez une erreur selon laquelle « Le serveur de rapports ne peut pas accéder aux données chiffrées » lors de la tentative d'ouverture d'une page de définition d'abonnement, ou si vous êtes invité à entrer des informations d'identification lorsque vous ouvrez un rapport qui utilisait précédemment les informations d'identification stockées pour la source de données du rapport, vous avez restauré une clé non valide.  
  
 Si vous restaurez une clé non valide différente de celle utilisée pour chiffrer les données, il est impossible de déchiffrer les données actuellement stockées dans la base de données du serveur de rapports. Si vous restaurez une clé non valide, vous devez restaurer immédiatement une copie de sauvegarde de la clé correcte, si elle est disponible. Si vous ne disposez pas de la copie de sauvegarde de la clé utilisée pour chiffrer les données, vous devez supprimer toutes les données chiffrées. À cette fin, cliquez sur le bouton **Supprimer** de la page [Clés de chiffrement](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md) . Après avoir supprimé le contenu chiffré, vous devez mettre à jour tous les abonnements manuellement et spécifier à nouveau toutes les informations d'identification stockées définies pour les rapports et les abonnements pilotés par les données sur le serveur de rapports.  
  
## <a name="restore-encryption-key-dialog"></a>Boîte de dialogue Restaurer la clé de chiffrement  
 Pour plus d’informations sur où trouver le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager, consultez [Gestionnaire de Configuration de Reporting Services &#40;en Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 Pour ouvrir la boîte de dialogue Restaurer la clé de chiffrement, cliquez sur **Clés de chiffrement** dans le volet de navigation du Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , puis cliquez sur **Restaurer**. La boîte de dialogue apparaît également lorsque vous mettez à jour le compte de service à l'aide de la page Compte de service du Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d'informations sur  
  
## <a name="options"></a>Options  
 **Emplacement du fichier**  
 Sélectionnez le fichier protégé par mot de passe qui contient une copie de la clé symétrique. L'extension de fichier par défaut est .snk.  
  
 **Mot de passe**  
 Entrez le mot de passe permettant de déverrouiller le fichier. Seuls les utilisateurs qui connaissent le mot de passe peuvent restaurer la clé. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applique une stratégie de mot de passe fort. Le mot de passe doit contenir au moins 8 caractères et inclure une combinaison de caractères alphanumériques majuscules et minuscules, ainsi qu'au moins un caractère symbole.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques d’aide F1 Gestionnaire de Configuration de Reporting Services &#40;SSRS en Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Sauvegarder et restaurer les clés de chiffrement Reporting Services](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)   
 [Supprimer et recréer des clés de chiffrement &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-delete-and-re-create-encryption-keys.md)   
 [Initialiser un serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server.md)   
 [Stocker des données chiffrées du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Clés de chiffrement &#40;SSRS en Mode natif&#41;](../../../2014/sql-server/install/encryption-keys-ssrs-native-mode.md)  
  
  
