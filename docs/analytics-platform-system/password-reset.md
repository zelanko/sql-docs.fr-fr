---
title: Réinitialisation du mot de passe
description: La page réinitialisation du mot de passe vous permet de modifier le mot de passe des comptes d’administrateur utilisés par Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 952dbda04b4f7132406e3a6de4479afea1be92e7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74400903"
---
# <a name="password-reset---analytics-platform-system"></a>Réinitialisation de mot de passe-système de plateforme d’analyse
La page **réinitialisation du mot de passe** vous permet de modifier le mot de passe des comptes d’administrateur utilisés par Analytics Platform System.  
  
> [!WARNING]  
> Utilisez toujours le **Configuration Manager** pour mettre à jour le mot de passe administrateur de domaine de l’appliance. D’autres méthodes peuvent ne pas mettre à jour tous les composants d’Analytics Platform System et provoquer des problèmes d’accès aux appliances.  
  
Les mots de passe du système de plateforme d’analyse vous sont attribués lorsque l’appliance est livrée. Remplacez toujours les mots de passe par de nouvelles valeurs lorsque vous assumez la responsabilité de votre appliance. Il y a trois mots de passe à mettre à jour. Il n’est pas nécessaire que les mots de passe soient les mêmes.  
  
**F<*xxxx*> \Administrateur**  
**Administrateur** du domaine de l’appliance.  
  
**.\Administrator**  
Compte d' **administrateur** local sur les ordinateurs qui hébergent les ordinateurs virtuels.  
  
> [!IMPORTANT]  
> Pour la mise à jour d’appliance 1, **Configuration Manager** ne modifie pas correctement le mot de passe des comptes d’administrateur local sur tous les ordinateurs virtuels PDW. Si nécessaire, contactez le code CSS pour obtenir des instructions supplémentaires.  
  
**sa**  
Connexion **sa** dans SQL Server. **sa** est membre du rôle serveur fixe **sysadmin** et est un administrateur SQL Server. Le mot de passe de la connexion **sa** peut également être modifié à l’aide de l’instruction **ALTER LOGIN** .  
  
## <a name="password-requirements"></a>Exigences de mot de passe  
Les informations d’identification d’administrateur de domaine et les informations d’identification d’administrateur système adhèrent aux stratégies de force de mot de passe pour chaque type d’informations d’identification. Lorsque vous modifiez les informations d’identification d’administrateur de domaine, le nouveau mot de passe est mis à jour vers le domaine, le cas échéant, dans SQL Server PDW.  
  
> [!IMPORTANT]  
> SQL Server PDW ne prend pas en charge le caractère de**$** signe dollar () dans les mots de passe d’administrateur de domaine ou d’administrateur local. Les caractères **^% &** sont autorisés dans les mots de passe, mais PowerShell les considère comme des caractères spéciaux. Si l’un de ces caractères est utilisé dans les mots de passe pour l’administrateur système ou les comptes**sa** SQL Server (les paramètres **AdminPassword** et **PdwSAPassword** lors de l’installation), le programme d’installation, y compris l’installation, la mise à niveau, l’REPLACENODE et la mise à jour corrective, échouera. Pour garantir la réussite de la mise à niveau lorsque les mots de passe actuels contiennent des caractères non pris en charge, modifiez ces mots de passe afin qu’ils ne contiennent pas ces caractères avant d’exécuter la mise à niveau. Une fois la mise à niveau terminée, vous pouvez rétablir les valeurs d’origine de ces mots de passe. Pour plus d’informations sur les exigences relatives aux mots de passe, consultez [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md).  
  
## <a name="to-reset-a-password"></a>Pour réinitialiser un mot de passe  
  
1.  Connectez-vous au nœud de contrôle et lancez le **Configuration Manager** (**dwconfig. exe**). Pour plus d’informations, consultez [la page lancement du&#41;Configuration Manager &#40;Analytics Platform System ](launch-the-configuration-manager.md).  
  
2.  Dans le volet gauche de la **Configuration Manager**, cliquez sur **réinitialisation du mot de passe**.  
  
3.  Sélectionnez le type d’administrateur dans le menu déroulant **compte** , puis entrez le nouveau mot de passe dans les zones **mot** de passe et **confirmer le mot de passe** . Cliquez sur **appliquer** pour enregistrer vos modifications.  
  
    Les modifications que vous apportez à ces comptes n’affectent pas les sessions actuellement actives, mais elles sont appliquées lors de la tentative de connexion suivante pour chaque utilisateur.  
  
    ![Mot de passe SQL Server DWConfig](./media/password-reset/SQL_Server_PDW_DWConfig_TopPW.png "SQL_Server_PDW_DWConfig_TopPW")  
  
## <a name="see-also"></a>Voir aussi  
[Définissez le mot de passe d’administrateur pour la connexion aux nœuds AD en mode de restauration des services d’annuaire &#40;DSRM&#41; &#40;Analytics Platform System&#41;](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md)  
[Lancez le système de plateforme Configuration Manager &#40;Analytics&#41;](launch-the-configuration-manager.md)  
  
