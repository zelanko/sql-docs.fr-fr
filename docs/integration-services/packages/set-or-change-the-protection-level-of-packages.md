---
title: "D&#233;finir ou modifier le niveau de protection des packages | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mots de passe [Integration Services]"
  - "packages [Integration Services], sécurité"
  - "sécurité [Integration Services], niveaux de protection"
  - "niveau de protection des packages [Integration Services]"
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# D&#233;finir ou modifier le niveau de protection des packages
  Pour contrôler l’accès au contenu des packages et aux valeurs sensibles qu’ils contiennent, telles que les mots de passe, définissez la valeur de la propriété **ProtectionLevel**. Les packages contenus dans un projet doivent avoir le même niveau de protection que le projet pour permettre sa génération. Si vous modifiez le paramètre de propriété **ProtectionLevel** du projet, vous devez mettre à jour manuellement le paramètre de propriété des packages.  
  
 Pour plus d’informations sur la façon de déterminer les paramètres **ProtectionLevel** adaptés à vos packages à différentes étapes du cycle de vie de package, consultez [Contrôle d’accès pour les données sensibles présentes dans les packages](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md). Pour obtenir une vue d’ensemble des fonctionnalités de sécurité dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Vue d’ensemble de la sécurité &#40;Integration Services&#41;](../../integration-services/security/security-overview-integration-services.md).  
  
 Les procédures dans cette rubrique décrivent comment utiliser [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou l’utilitaire en ligne de commande dtutil pour modifier la propriété **ProtectionLevel**.  
  
> [!NOTE]  
>  En plus des procédures dans cette rubrique, vous pouvez en général définir ou modifier la propriété **ProtectionLevel** d’un package quand vous importez ou exportez le package. Vous pouvez également modifier la propriété **ProtectionLevel** d’un package quand vous utilisez l’Assistant Importation et exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour enregistrer un package.  
  
### Pour définir ou modifier le niveau de protection d'un package dans les outils de données SQL Server  
  
1.  Examinez les valeurs disponibles pour la propriété **ProtectionLevel** dans la rubrique [Définition du niveau de protection des packages](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md) et déterminez la valeur appropriée pour votre package.  
  
2.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient le package.  
  
3.  Ouvrez le package dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
4.  Si la fenêtre Propriétés n'affiche pas les propriétés du package, cliquez sur l'aire de conception.  
  
5.  Dans la fenêtre Propriétés, dans le groupe **Sécurité**, sélectionnez la valeur appropriée pour la propriété **ProtectionLevel**.  
  
     Si vous sélectionnez un niveau de protection qui requiert un mot de passe, entrez le mot de passe comme valeur de la propriété **PackagePassword**.  
  
6.  Dans le menu **Fichier**, sélectionnez **Enregistrer les éléments sélectionnés** pour enregistrer le package modifié.  
  
### Pour définir ou modifier le niveau de protection de package à l'invite de commandes  
  
1.  Examinez les valeurs disponibles pour la propriété **ProtectionLevel** dans la rubrique [Définition du niveau de protection des packages](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md) et déterminez la valeur appropriée pour votre package.  
  
2.  Examinez les mappages pour l’option **Encrypt** dans la rubrique [Utilitaire dtutil](../../integration-services/dtutil-utility.md) et déterminez l’entier approprié à utiliser comme valeur de la propriété **ProtectionLevel** sélectionnée.  
  
3.  Ouvrez une fenêtre d'invite de commandes.  
  
4.  À l’invite de commandes, naviguez jusqu’au dossier qui contient le ou les packages pour lesquels vous souhaitez définir la propriété **ProtectionLevel**.  
  
     Les exemples de syntaxe affichés à l'étape suivante supposent que ce dossier est le dossier actif.  
  
5.  Définissez ou modifiez le niveau de protection des packages en utilisant une commande semblable à celle des exemples suivants :  
  
    -   La commande suivante définit la propriété **ProtectionLevel** d’un package dans le système de fichiers au niveau 2, « Chiffrer les données sensibles avec un mot de passe », avec le mot de passe « strongpassword » :  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   La commande suivante définit la propriété **ProtectionLevel** de tous les packages dans un dossier spécifique dans le système de fichiers au niveau 2, « Chiffrer les données sensibles avec un mot de passe », avec le mot de passe « strongpassword » :  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         Si vous utilisez une commande semblable dans un fichier de commandes, entrez l'espace réservé de fichier, « % f », comme « %% f » dans le fichier de commandes.  
  
## Voir aussi  
 [Utilitaire dtutil](../../integration-services/dtutil-utility.md)  
  
  