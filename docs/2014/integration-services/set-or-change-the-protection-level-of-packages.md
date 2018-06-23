---
title: Définir ou modifier le niveau de Protection de Packages | Documents Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- passwords [Integration Services]
- packages [Integration Services],security
- security [Integration Services],protection levels
- protection level for packages [Integration Services]
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 695667f3ba50b6cde3d2b9629e7116fecf7c4b16
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143929"
---
# <a name="set-or-change-the-protection-level-of-packages"></a>Définir ou modifier le niveau de protection des packages
  Pour contrôler l'accès au contenu des packages et aux valeurs sensibles qu'ils contiennent, telles que les mots de passe, définissez la valeur de la propriété `ProtectionLevel`. Les packages contenus dans un projet doivent avoir le même niveau de protection que le projet pour permettre sa génération. Si vous modifiez le paramètre de propriété `ProtectionLevel` du projet, vous devez mettre à jour manuellement le paramètre de propriété des packages.  
  
 Pour plus d’informations sur la façon de déterminer la `ProtectionLevel` paramètres appropriés pour vos packages à différents stades dans le cycle de vie de package, consultez [le contrôle d’accès pour les données sensibles dans des Packages](security/access-control-for-sensitive-data-in-packages.md). Pour obtenir une vue d’ensemble des fonctionnalités de sécurité dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], consultez [Vue d’ensemble de la sécurité &#40;Integration Services&#41;](security/security-overview-integration-services.md).  
  
 Les procédures décrites dans cette rubrique décrivent comment utiliser [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ou l’utilitaire d’invite de commande dtutil pour modifier le `ProtectionLevel` propriété.  
  
> [!NOTE]  
>  En plus des procédures dans cette rubrique, vous pouvez en général définir ou modifier le `ProtectionLevel` propriété d’un package lorsque vous importez ou exportez le package. Vous pouvez également modifier la propriété `ProtectionLevel` d'un package lorsque vous utilisez l'Assistant Importation et exportation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour enregistrer un package.  
  
### <a name="to-set-or-change-the-protection-level-of-a-package-in-sql-server-data-tools"></a>Pour définir ou modifier le niveau de protection d'un package dans les outils de données SQL Server  
  
1.  Passez en revue les valeurs disponibles pour le `ProtectionLevel` propriété dans la rubrique [définissant le niveau de Protection de Packages](security/access-control-for-sensitive-data-in-packages.md)et déterminer la valeur appropriée pour votre package.  
  
2.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui contient le package.  
  
3.  Ouvrez le package dans le Concepteur [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
4.  Si la fenêtre Propriétés n'affiche pas les propriétés du package, cliquez sur l'aire de conception.  
  
5.  Dans la fenêtre Propriétés, dans le **sécurité** groupe, sélectionnez la valeur appropriée pour le `ProtectionLevel` propriété.  
  
     Si vous sélectionnez un niveau de protection qui requiert un mot de passe, entrez le mot de passe comme valeur de la propriété **PackagePassword** .  
  
6.  Dans le menu **Fichier** , sélectionnez **Enregistrer les éléments sélectionnés** pour enregistrer le package modifié.  
  
### <a name="to-set-or-change-the-protection-level-of-packages-at-the-command-prompt"></a>Pour définir ou modifier le niveau de protection de package à l'invite de commandes  
  
1.  Passez en revue les valeurs disponibles pour le `ProtectionLevel` propriété dans la rubrique [définissant le niveau de Protection de Packages](security/access-control-for-sensitive-data-in-packages.md)et déterminer la valeur appropriée pour votre package.  
  
2.  Examinez les mappages pour les `Encrypt` option dans la rubrique [utilitaire dtutil](dtutil-utility.md)et déterminez l’entier approprié à utiliser en tant que la valeur de l’élément sélectionné `ProtectionLevel` propriété.  
  
3.  Ouvrez une fenêtre d'invite de commandes.  
  
4.  À l’invite de commandes, accédez au dossier qui contient l’ou les packages pour lesquels vous souhaitez définir le `ProtectionLevel` propriété.  
  
     Les exemples de syntaxe affichés à l'étape suivante supposent que ce dossier est le dossier actif.  
  
5.  Définissez ou modifiez le niveau de protection des packages en utilisant une commande semblable à celle des exemples suivants :  
  
    -   La commande suivante définit le `ProtectionLevel` propriété d’un package individuel dans le système de fichiers au niveau 2, « Chiffrer les données sensibles avec un mot de passe », le mot de passe « strongpassword » :  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   La commande suivante définit la propriété `ProtectionLevel` de tous les packages dans un dossier spécifique dans le système de fichiers au niveau 2, « Chiffrer les données sensibles avec un mot de passe », avec le mot de passe « strongpassword » :  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         Si vous utilisez une commande semblable dans un fichier de commandes, entrez l'espace réservé de fichier, « % f », comme « %% f » dans le fichier de commandes.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire dtutil](dtutil-utility.md)  
  
  