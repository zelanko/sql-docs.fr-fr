---
title: Configurer un compte de service (SSRS Configuration Manager) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Report Server Web service, accounts
- service accounts [Reporting Services]
- Report Server Windows service, accounts
- Web service [Reporting Services], report server
ms.assetid: 25000ad5-3f80-4210-8331-d4754dc217e0
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 04dff943d1227f84ff514e593f65c2ce4d7a918f
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952582"
---
# <a name="configure-a-service-account-ssrs-configuration-manager"></a>Configurer un compte de service (Gestionnaire de configuration de SSRS)
  Dans une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], le service Web Report Server, le Gestionnaire de rapports et l'application de traitement en arrière-plan s'exécutent au sein d'un même service. Le compte sous lequel le service s'exécute est défini pendant l'installation lorsque vous spécifiez le compte dans la page Identité du service, mais vous pouvez utiliser l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] si vous souhaitez utiliser un autre compte ou mettre à jour le mot de passe.  
  
 Si vous disposez d’un serveur de rapports configuré pour utiliser le mode intégré SharePoint et que vous modifiez le compte de service à l’aide de l’outil de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous devez également ouvrir l’administration centrale de SharePoint et utiliser l’accès à la **base de données** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. pour réappliquer les paramètres du serveur de rapports et de l’instance. Cette étape permet d’accorder au nouveau compte de service l’accès aux bases de données SharePoint, ce qui est nécessaire pour intégrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] avec [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] ou [!INCLUDE[SPS2010](../../includes/sps2010-md.md)].  
  
 Utilisez toujours l'outil de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour mettre à jour le compte de service afin que les autres paramètres qui dépendent de l'identité de service puissent être mis à jour simultanément.  
  
> [!NOTE]  
>  Les comptes de service Windows intégrés (Service local ou Service réseau) ne sont pas pris en charge comme comptes de service du serveur de rapports sur un ordinateur qui est contrôleur de domaine.  
  
 Procédures  
  
### <a name="to-configure-the-report-server-service-account"></a>Pour configurer le compte de service Report Server  
  
1.  Démarrez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , puis connectez-vous au serveur de rapports.  
  
2.  Dans la page Compte de service, sélectionnez l'option qui décrit le type de compte que vous souhaitez utiliser. Pour obtenir des recommandations sur le type de compte à spécifier, consultez [configurer le compte &#40;de service&#41;du serveur de rapports SSRS Configuration Manager](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md).  
  
3.  Si vous avez sélectionné un compte d'utilisateur Windows, spécifiez le nouveau compte et le nouveau mot de passe. La longueur du nom du compte ne peut pas excéder 20 caractères.  
  
     Si le serveur de rapports est déployé dans un réseau qui prend en charge l'authentification Kerberos, vous devez inscrire le nom de principal du service (SPN) du serveur de rapports avec le compte d'utilisateur de domaine que vous venez de spécifier. Pour plus d’informations, consultez [Inscrire un nom de principal du service &#40;SPN&#41; pour un serveur de rapports](../../reporting-services/report-server/register-a-service-principal-name-spn-for-a-report-server.md).  
  
4.  Cliquez sur **Appliquer**.  
  
5.  Lorsque vous êtes invité à sauvegarder la clé symétrique, tapez un nom de fichier et un emplacement pour la sauvegarde de la clé symétrique, entrez un mot de passe pour verrouiller et déverrouiller le fichier, puis cliquez sur **OK**.  
  
6.  Si le serveur de rapports utilise le compte de service pour se connecter à la base de données du serveur de rapports, les informations de connexion seront mises à jour pour utiliser le nouveau compte ou mot de passe. La mise à jour des informations de connexion nécessite que vous vous connectiez à la base de données. Si la boîte de dialogue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] apparaît, entrez les informations d’identification habilitées à se connecter à la **base de données**, puis cliquez sur **OK**.  
  
7.  Lorsque vous êtes invité à restaurer la clé symétrique, tapez le mot de passe spécifié à l’étape 5, puis cliquez sur **OK**.  
  
8.  Examinez les messages d'état dans le volet Résultats pour vérifier que toutes les tâches se sont terminées avec succès.  
  
## <a name="troubleshooting-service-identity-update-errors"></a>Dépannage des erreurs de mise à jour de l'identité du service  
 La modification de l'identité du service initialise une série d'événements qui incluent le redémarrage du service, la mise à jour de la clé de chiffrement protégée par mot de passe, la mise à jour des réservations d'URL et la mise à jour des informations de connexion à la base de données du serveur de rapports si vous utilisez le compte de service pour vous connecter à la base de données du serveur de rapports. Vous pouvez surveiller l'état de ces événements en consultant les notifications dans le volet Résultats en bas de page. Si des erreurs se produisent pendant ce processus, vous pouvez essayer de les résoudre à l'aide des techniques suivantes :  
  
-   Si la clé symétrique ne peut pas être restaurée, vous pouvez essayer de la restaurer manuellement en utilisant **Restaurer** dans la page Clés de chiffrement. Si cette technique ne fonctionne pas, envisagez de supprimer le contenu chiffré. Vous devrez recréer les abonnements et les informations de connexion à la source de données, mais le reste du contenu demeurera disponible. Pour plus d’informations, consultez [Back Up and Restore Reporting Services Encryption Keys](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).  
  
-   Si le service ne démarre pas, redémarrez-le manuellement en utilisant l'application console Services dans les Outils d'administrateur.  
  
-   Les erreurs de réservation d'URL peuvent se produire lorsque vous mettez à jour le compte de service. Chaque réservation d'URL comporte un descripteur de sécurité incluant une liste de contrôle d'accès discrétionnaire (DACL) qui accorde l'autorisation au compte de service d'accepter les demandes sur l'URL. Lorsque vous mettez à jour le compte, l'URL doit être recréée pour mettre à jour la liste DACL avec les nouvelles informations de compte. Si la réservation d'URL ne peut pas être recréée et que vous savez que le compte est valide, essayez de redémarrer l'ordinateur. Si l'erreur persiste, essayez d'utiliser un autre compte.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Configurer le compte de service Report Server &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Configurer une connexion à la base de données du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../../2014/sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Compte &#40;de service SSRS en&#41;mode natif](../../../2014/sql-server/install/service-account-ssrs-native-mode.md)   
 [Configurer et gérer des clés de chiffrement &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  
  
  
