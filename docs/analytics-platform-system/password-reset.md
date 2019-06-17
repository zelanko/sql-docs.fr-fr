---
title: Réinitialisation de mot de passe - Analytique Platform System | Microsoft Docs
description: La page de réinitialisation de mot de passe vous permet de modifier le mot de passe pour les comptes d’administrateur utilisé par le système de plateforme d’Analytique.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 63fbb097bf1ca926223ce7c0114c8da5d10cd969
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62639955"
---
# <a name="password-reset---analytics-platform-system"></a>Réinitialisation de mot de passe - Analytique Platform System
Le **mot de passe réinitialisé** page vous permet de modifier le mot de passe pour les comptes d’administrateur utilisé par le système de plateforme d’Analytique.  
  
> [!WARNING]  
> Utilisez toujours le **Configuration Manager** pour mettre à jour le mot de passe administrateur de domaine appliance. Autres méthodes ne peuvent pas mettre à jour tous les composants du système de plateforme d’Analytique et peut entraîner des problèmes d’accès appliance.  
  
Lorsque l’appliance est remise, vous obtenez les mots de passe Analytique Platform System. Toujours modifier les mots de passe pour les nouvelles valeurs lorsque vous prenez la responsabilité de votre appliance. Il existe trois mots de passe pour mettre à jour. Les mots de passe n’ont pas à être identique à l’autre.  
  
**F <*xxxx*> \Administrator**  
Le **administrateur** du domaine d’application.  
  
**.\Administrator**  
Local **administrateur** compte sur les ordinateurs qui hébergent les machines virtuelles.  
  
> [!IMPORTANT]  
> Pour l’appliance update 1, **Configuration Manager** ne modifie pas correctement le mot de passe des comptes d’administrateur local tout au long de la PDW VM. Si cela est nécessaire, contactez Microsoft pour obtenir des instructions supplémentaires.  
  
**sa**  
Le **sa** connexion dans SQL Server. **sa** est un membre de la **sysadmin** rôle serveur fixe et est un administrateur de SQL Server. Le mot de passe de la **sa** connexion peut également être modifiée à l’aide de la **ALTER LOGIN** instruction.  
  
## <a name="password-requirements"></a>Exigences de mot de passe  
Les informations d’identification administrateur de domaine et les informations d’identification d’administrateur système conformes aux stratégies de force de mot de passe pour chaque type d’informations d’identification. Lorsque vous modifiez les informations d’identification administrateur de domaine, le nouveau mot de passe est mis à jour au domaine lorsque cela est nécessaire tout au long de SQL Server PDW.  
  
> [!IMPORTANT]  
> SQL Server PDW ne prend pas en charge le caractère de signe dollar ( **$** ) dans l’administrateur de domaine ou les mots de passe d’administrateur local. Les caractères **^ % &** sont autorisés dans les mots de passe, mais PowerShell considère comme des caractères spéciaux. Si aucun de ces caractères sont utilisés dans les mots de passe pour l’administrateur système ou d’un SQL Server**sa** comptes (le **AdminPassword** et **PdwSAPassword** paramètres lors de la le programme d’installation), configurer, y compris installation, mise à niveau, REPLACENODE et une mise à jour corrective, échoue. Pour garantir une mise à niveau lorsque les mots de passe actuels contient des caractères non pris en charge, modifier ces mots de passe afin qu’ils ne contiennent pas ces caractères avant d’exécuter la mise à niveau. Une fois la mise à niveau terminée, vous pouvez définir ces mots de passe à leurs valeurs d’origine. Pour plus d’informations sur les exigences de mot de passe, consultez [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md).  
  
## <a name="to-reset-a-password"></a>Pour réinitialiser un mot de passe  
  
1.  Se connecter sur le nœud de contrôle et lancez le **Configuration Manager** (**dwconfig.exe**). Pour plus d’informations, consultez [lancer le Gestionnaire de Configuration &#40;Analytique Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Dans le volet gauche de la **Configuration Manager**, cliquez sur **réinitialisation de mot de passe**.  
  
3.  Sélectionner le type d’administrateur dans le **compte** menu déroulant, puis entrez le nouveau mot de passe dans le **mot de passe** et **confirmer le mot de passe** cases. Cliquez sur **appliquer** pour enregistrer vos modifications.  
  
    Modifications apportées à ces comptes n’affectent pas les sessions actuellement actives, mais s’appliquera à la prochaine tentative d’ouverture de session pour chaque utilisateur.  
  
    ![Mot de passe SQL Server DWConfig](./media/password-reset/SQL_Server_PDW_DWConfig_TopPW.png "SQL_Server_PDW_DWConfig_TopPW")  
  
## <a name="see-also"></a>Voir aussi  
[Définir le mot de passe administrateur pour vous connecter à des nœuds AD dans Directory Services Restore Mode &#40;DSRM&#41; &#40;Analytique Platform System&#41;](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md)  
[Lancez le Gestionnaire de Configuration &#40;Analytique Platform System&#41;](launch-the-configuration-manager.md)  
  
