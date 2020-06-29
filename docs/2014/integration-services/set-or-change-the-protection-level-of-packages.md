---
title: Définir ou modifier le niveau de protection des packages | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ae909a1f7a61c5ae2aa3d6319fd03c54dd70b0e1
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85421826"
---
# <a name="set-or-change-the-protection-level-of-packages"></a>Définir ou modifier le niveau de protection des packages
  Pour contrôler l'accès au contenu des packages et aux valeurs sensibles qu'ils contiennent, telles que les mots de passe, définissez la valeur de la propriété `ProtectionLevel`. Les packages contenus dans un projet doivent avoir le même niveau de protection que le projet pour permettre sa génération. Si vous modifiez le paramètre de propriété `ProtectionLevel` du projet, vous devez mettre à jour manuellement le paramètre de propriété des packages.  
  
 Pour plus d’informations sur la façon de déterminer les `ProtectionLevel` paramètres appropriés pour vos packages à différentes étapes du cycle de vie d’un package, consultez [Access Control pour obtenir des données sensibles dans des packages](security/access-control-for-sensitive-data-in-packages.md). Pour obtenir une vue d’ensemble des fonctionnalités de sécurité dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], consultez [Vue d’ensemble de la sécurité &#40;Integration Services&#41;](security/security-overview-integration-services.md).  
  
 Les procédures dans cette rubrique décrivent comment utiliser [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ou l'utilitaire en ligne de commande dtutil pour modifier la propriété `ProtectionLevel`.  
  
> [!NOTE]  
>  En plus des procédures dans cette rubrique, vous pouvez en général définir ou modifier la propriété `ProtectionLevel` d'un package lorsque vous importez ou exportez le package. Vous pouvez également modifier la propriété `ProtectionLevel` d'un package lorsque vous utilisez l'Assistant Importation et exportation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour enregistrer un package.  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a>Pour définir ou modifier le niveau de protection d'un package dans les outils de données SQL Server  
  
1.  Passez en revue les valeurs disponibles pour la `ProtectionLevel` propriété dans la rubrique [définition du niveau de protection des packages](security/access-control-for-sensitive-data-in-packages.md)et déterminez la valeur appropriée pour votre package.  
  
2.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui contient le package.  
  
3.  Ouvrez le package dans le Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
4.  Si la fenêtre Propriétés n'affiche pas les propriétés du package, cliquez sur l'aire de conception.  
  
5.  Dans le Fenêtre Propriétés, dans le groupe **sécurité** , sélectionnez la valeur appropriée pour la `ProtectionLevel` propriété.  
  
     Si vous sélectionnez un niveau de protection qui requiert un mot de passe, entrez le mot de passe comme valeur de la propriété **PackagePassword** .  
  
6.  Dans le menu **Fichier** , sélectionnez **Enregistrer les éléments sélectionnés** pour enregistrer le package modifié.  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a>Pour définir ou modifier le niveau de protection de package à l'invite de commandes  
  
1.  Passez en revue les valeurs disponibles pour la `ProtectionLevel` propriété dans la rubrique [définition du niveau de protection des packages](security/access-control-for-sensitive-data-in-packages.md)et déterminez la valeur appropriée pour votre package.  
  
2.  Passez en revue les mappages de l' `Encrypt` option dans la rubrique [Utilitaire dtutil](dtutil-utility.md)et déterminez l’entier approprié à utiliser comme valeur de la `ProtectionLevel` propriété sélectionnée.  
  
3.  Ouvrez une fenêtre d’invite de commandes.  
  
4.  À l'invite de commandes, naviguez jusqu'au dossier qui contient le ou les packages pour lesquels vous souhaitez définir la propriété `ProtectionLevel`.  
  
     Les exemples de syntaxe affichés à l'étape suivante supposent que ce dossier est le dossier actif.  
  
5.  Définissez ou modifiez le niveau de protection des packages en utilisant une commande semblable à celle des exemples suivants :  
  
    -   La commande suivante définit la propriété `ProtectionLevel` d'un package dans le système de fichiers au niveau 2, « Chiffrer les données sensibles avec un mot de passe », avec le mot de passe « strongpassword » :  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   La commande suivante définit la propriété `ProtectionLevel` de tous les packages dans un dossier spécifique dans le système de fichiers au niveau 2, « Chiffrer les données sensibles avec un mot de passe », avec le mot de passe « strongpassword » :  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         Si vous utilisez une commande semblable dans un fichier de commandes, entrez l'espace réservé de fichier, « % f », comme « %% f » dans le fichier de commandes.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire dtutil](dtutil-utility.md)  
  
  
