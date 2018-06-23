---
title: Configuration du moteur de base de données - compte de configuration | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 834b26bc-49de-4033-88d5-6aa7b1609720
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4377f3eb668f78cdf29b886acf22549e1e5be0aa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044404"
---
# <a name="database-engine-configuration---account-provisioning"></a>Configuration du moteur de base de données – Mise en service de compte
  Utilisez cette page pour définir le mode de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et ajouter des utilisateurs Windows ou des groupes comme administrateurs du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="considerations-for-running-includesscurrentincludessscurrent-mdmd"></a>Éléments à prendre en considération pour l'exécution de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 Dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le groupe **BUILTIN\Administrators** était fourni en tant que compte de connexion du [!INCLUDE[ssDE](../../includes/ssde-md.md)] et les membres du groupe Administrateurs local pouvaient se connecter en utilisant leurs informations d’identification d’administrateur. L'utilisation d'autorisations élevées n'est pas recommandée. Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , le groupe **BUILTIN\Administrators** n’est pas fourni en tant que compte de connexion. Par conséquent, vous devez créer une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour chaque utilisateur administrateur et ajouter ce nom de connexion au rôle serveur fixe sysadmin lors de l'installation d'une nouvelle instance de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Vous devez procéder de même pour les comptes Windows utilisés pour exécuter les travaux de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Ceux-ci incluent les travaux de l'agent de réplication.  
  
## <a name="options"></a>Options  
 **Mode de sécurité** - Sélectionnez l’authentification Windows ou l’authentification en mode mixte pour votre installation.  
  
 **Configuration du principal Windows** - Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le groupe local de Windows Builtin\Administrator a été placé dans le rôle serveur sysadmin de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , en accordant aux administrateurs Windows l’accès à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], le groupe Builtin\Administrator n'est pas configuré dans le rôle serveur sysadmin. Au lieu de cela, vous devez configurer de manière explicite des administrateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les nouvelles installations lors de l'installation.  
  
> [!IMPORTANT]  
>  Vous devez configurer de manière explicite des administrateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les nouvelles installations lors de l'installation. L'installation ne vous permet pas de continuer tant que cette étape n'a pas été effectuée.  
  
 **Spécifier les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]administrateurs** - Vous devez spécifier au moins un principal Windows pour l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour ajouter le compte sous lequel le programme d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécute, cliquez sur le bouton **Utilisateur actuel**. Pour ajouter ou supprimer des comptes dans la liste des administrateurs système, cliquez sur **Ajouter** ou sur **Supprimer**, puis modifiez la liste des utilisateurs, groupes ou ordinateurs qui disposeront des privilèges d'administrateur pour l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Lorsque vous avez terminé de modifier la liste, cliquez sur **OK**, puis vérifiez la liste des administrateurs dans la boîte de dialogue de configuration. Une fois la liste complète, cliquez sur **Suivant**.  
  
 Si vous sélectionnez l'authentification de mode mixte, vous devez fournir les informations d'identification de session pour le compte de l'administrateur système (SA) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] intégré.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
 **Mode d’authentification Windows**  
 Quand un utilisateur se connecte par le biais d'un compte d'utilisateur Windows, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide le nom et le mot de passe du compte à l'aide du jeton du principal Windows du système d'exploitation. Il s'agit du mode d'authentification par défaut et il est plus fiable que le mode mixte. L'authentification Windows utilise le protocole de sécurité Kerberos, met en œuvre les stratégies de mot de passe en termes de validation de la complexité des mots de passe forts et prend en charge le verrouillage des comptes et l'expiration des mots de passe.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)] Ne définissez jamais un mot de passe d'administrateur système (SA) vide ou faible.  
  
 **Mode mixte (authentification Windows ou authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])**  
 Permet aux utilisateurs de se connecter en utilisant l'authentification Windows ou l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les utilisateurs qui se connectent via un compte d'utilisateur Windows peuvent utiliser des connexions approuvées qui sont validées par Windows.  
  
 Si vous devez choisir l'authentification en mode mixte et utiliser des connexions SQL pour vous adapter à des applications héritées, définissez des mots de passe forts pour tous les comptes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  L'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est fournie uniquement dans un souci de compatibilité descendante. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 **Entrez le mot de passe**  
 Entrez et confirmez la connexion d'administrateur système (sa). Les mots de passe constituant la première ligne de défense contre les intrus, le choix de mots de passe forts est essentiel à la sécurité de votre système. Ne définissez jamais un mot de passe sa vide ou faible.  
  
> [!NOTE]  
>  Les mots de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent contenir de 1 à 128 caractères, constitués d’une combinaison quelconque de lettres, de symboles et de chiffres. Si vous choisissez l'authentification en mode mixte, vous devez d'abord entrer un mot de passe sa fort avant de passer à la page suivante de l'Assistant Installation.  
  
 **Instructions sur les mots de passe forts**  
 Les mots de passe forts ne peuvent pas être aisément devinés par une personne et ils ne sont pas aisément piratés par un programme informatique. Les mots de passe forts ne peuvent pas utiliser des conditions ou des termes interdits, notamment :  
  
-   Une condition vide ou NULL  
  
-   "Password"  
  
-   "Admin"  
  
-   "Administrator"  
  
-   "sa"  
  
-   "sysadmin"  
  
 Un mot de passe fort ne peut pas se composer des termes suivants associés à l'ordinateur d'installation :  
  
-   Le nom de l'utilisateur qui a ouvert la session sur l'ordinateur.  
  
-   Nom de l'ordinateur.  
  
 Un mot de passe fort doit contenir plus de 8 caractères et satisfaire au moins trois des quatre critères suivants :  
  
-   Il doit contenir des lettres majuscules.  
  
-   Il doit contenir des lettres minuscules.  
  
-   Il doit contenir des chiffres.  
  
-   Il doit contenir des caractères non alphanumériques, comme #, % ou ^.  
  
 Les mots de passe entrés sur cette page doivent répondre aux exigences des stratégies de mots de passe forts. Si vous avez un processus automatisé qui utilise l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , assurez-vous que le mot de passe répond aux exigences des stratégies de mots de passe forts.  
  
## <a name="related-content"></a>Contenu associé  
 Pour plus d'informations sur le choix de l'authentification Windows ou de l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez la rubrique **Choisir un mode d’authentification** dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour plus d’informations sur le choix d’un compte pour l’exécution de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], consultez la rubrique **Configurer les comptes de service Windows et les autorisations** dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  