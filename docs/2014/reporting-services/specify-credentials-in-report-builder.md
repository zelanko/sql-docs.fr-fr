---
title: Spécifiez les informations d’identification dans le Générateur de rapports | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7412ce68-aece-41c0-8c37-76a0e54b6b53
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 432b41216418cd1ad1bae70557c95a589f5e78dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66101137"
---
# <a name="specify-credentials-in-report-builder"></a>Spécifier des informations d’identification dans le Générateur de rapports
  Les informations d'identification permettent d'authentifier l'utilisateur qui tente de récupérer des données à partir d'une source de données. Le propriétaire de la source de données détermine le type d'informations d'identification à utiliser. Par exemple, un administrateur de base de données peut spécifier que l'utilisateur doit fournir un nom d'utilisateur et un mot de passe Windows.  
  
 Dans une définition de rapport, chaque définition de la source de données indique un nom, une chaîne de connexion, l'utilisation ou non de la sécurité intégrée, ainsi que l'invite à afficher si des informations d'identification sont requises mais qu'elles ne sont pas spécifiées. Les informations d'identification ne sont pas enregistrées dans la définition de rapport. Une fois qu'un rapport a été publié sur le serveur de rapports, les sources de données peuvent être gérées indépendamment d'une définition de rapport. Les propriétaires de sources de données peuvent spécifier des informations d'identification pour les sources de données incorporées et partagées sur le serveur de rapports.  
  
> [!NOTE]  
>  L'administrateur du serveur de rapports doit accorder les autorisations appropriées à un utilisateur pour lui permettre de parcourir le serveur de rapports afin de sélectionner des sources de données partagées ou des modèles, d'ouvrir ou d'enregistrer des rapports. Pour plus d’informations, consultez [installation, désinstallation et prise en charge du Générateur de rapports](../../2014/reporting-services/install-uninstall-and-report-builder-support.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
## <a name="understanding-when-credentials-are-used"></a>Présentation de l'utilisation des informations d'identification  
 Dans le Générateur de rapports, les informations d'identification sont souvent utilisées lorsque vous vous connectez à un serveur de rapports ou pour des tâches liées aux données, par exemple la création d'une source de données incorporée, l'exécution d'une requête de dataset ou l'affichage de l'aperçu d'un rapport. Les informations d'identification ne sont pas enregistrées dans le rapport. Elles sont gérées séparément sur le serveur de rapports ou sur le client local. La liste suivante décrit les types d'informations d'identification que vous devrez peut-être fournir, leur emplacement et leur utilisation :  
  
-   Informations d’identification du serveur de rapports que vous entrez dans la [boîte de dialogue Ouverture de session Reporting Services &#40;Générateur de rapports&#41;](report-builder/reporting-services-login-dialog-box-report-builder.md).  
  
     Lorsque vous enregistrez, publiez ou naviguez vers un serveur de rapports ou un site SharePoint pour la première fois, vous devez éventuellement entrer vos informations d'identification. Les informations d'identification que vous entrez sont utilisées jusqu'à la fin de la session du Générateur de rapports. Si vous choisissez d'enregistrer les informations d'identification, elles sont stockées de manière sécurisée avec vos paramètres utilisateur sur votre ordinateur. Dans les sessions ultérieures du Générateur de rapports, les informations d'identification enregistrées sont utilisées pour la connexion au même serveur de rapports ou site SharePoint. L'administrateur du serveur de rapports ou l'administrateur SharePoint spécifie le type des informations d'identification à utiliser.  
  
-   Informations d’identification de la source de données que vous entrez dans la [boîte de dialogue Propriétés de la source de données, Informations d’identification &#40;Générateur de rapports&#41;](../../2014/reporting-services/data-source-properties-dialog-box-credentials-report-builder.md) pour une source de données incorporée.  
  
     Ces informations d'identification sont utilisées par le serveur de rapports pour établir une connexion de données à la source de données externe. Pour certains types de sources de données, les informations d'identification peuvent être stockées de manière sécurisée sur le serveur de rapports. Ces informations d'identification permettent à d'autres utilisateurs d'exécuter le rapport sans fournir d'informations d'identification pour la connexion de données sous-jacente.  
  
-   Informations d’identification de la source de données que vous entrez dans la [Boîte de dialogue Entrez les informations d’identification pour la source de données &#40;Générateur de rapports&#41;](report-data/enter-data-source-credentials-dialog-box-report-builder.md) quand vous exécutez une requête de dataset, actualisez des champs de dataset ou affichez un aperçu du rapport.  
  
     Ces informations d'identification sont utilisées pour établir une connexion de données entre le Générateur de rapports et la source de données externe, ou pour afficher l'aperçu d'un rapport configuré pour demander la saisie des informations d'identification. Les informations d'identification que vous entrez dans cette boîte de dialogue ne sont pas stockées sur le serveur de rapports et ne sont pas accessibles à d'autres utilisateurs. Le Générateur de rapports met en cache les informations d'identification pendant la session de modification du rapport afin que vous n'ayez pas besoin de les entrer chaque fois que vous exécutez la requête ou que vous affichez l'aperçu du rapport.  
  
     Pour les sources de données partagées, utilisez l'option **Enregistrer mon mot de passe** afin d'enregistrer les informations d'identification localement avec vos paramètres utilisateur sur votre ordinateur. Le Générateur de rapports utilise les informations d'identification enregistrées chaque fois qu'une connexion est établie vers la source de données externe correspondante.  
  
 Pour plus d’informations, consultez [Boîte de dialogue Propriétés de la source de données, Général &#40;Générateur de rapports&#41;](../../2014/reporting-services/data-source-properties-dialog-box-general-report-builder.md) et [Aperçu des rapports dans le Générateur de rapports](report-builder/previewing-reports-in-report-builder.md).  
  
## <a name="types-of-credentials"></a>Types d'informations d'identification  
 Le type d'informations d'identification pris en charge par une source de données est spécifié par le propriétaire de la source de données. Par exemple, vous devrez peut-être fournir un nom d'utilisateur de compte de connexion [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et un mot de passe correspondant pour accéder à une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Pour accéder à une autre source de données, vous devrez peut-être fournir un nom d'utilisateur et un mot de passe Windows. Il est possible que certaines sources de données ne requièrent pas d'informations d'identification.  
  
### <a name="options-for-specifying-credentials"></a>Options de spécification des informations d'identification  
 Les options suivantes permettent de spécifier des informations d'identification pour une source de données :  
  
-   Utiliser l'utilisateur Windows actuel (également appelée sécurité intégrée).  
  
-   Utiliser un nom d'utilisateur et un mot de passe enregistrés.  
  
-   Inviter l'utilisateur à fournir des informations d'identification.  
  
-   Aucune information d'identification n'est requise.  
  
### <a name="windows-integrated-security"></a>Sécurité intégrée de Windows  
 Lorsque vous sélectionnez **Utiliser l'authentification Windows (sécurité intégrée)** , le jeton de sécurité de l'utilisateur actuel est passé à la source de données. Dans ce cas, l'utilisateur n'est pas invité à taper son nom d'utilisateur ou son mot de passe. En règle générale, cette option requiert l'activation des fonctionnalités de délégation. Si ces fonctionnalités ne sont pas activées, vous ne pouvez utiliser cette option que pour accéder à une source de données située sur le même ordinateur.  
  
### <a name="user-name-and-password-login"></a>Connexion à l'aide d'un nom d'utilisateur et d'un mot de passe  
 Lorsque vous sélectionnez **Utiliser ce nom d'utilisateur et ce mot de passe**, un nom d'utilisateur et un mot de passe doivent être fournis pour permettre l'accès à la source de données. Pour une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , les informations d'identification peuvent correspondre à une connexion de base de données. Les informations d'identification sont passées à la source de données pour authentification.  
  
### <a name="prompted-credentials"></a>Informations d'identification demandées par invite  
 Lorsque vous spécifiez l'invite des informations d'identification, chaque utilisateur qui accède au rapport doit entrer un nom d'utilisateur et un mot de passe pour récupérer les données. Cette option est recommandée pour les rapports qui contiennent des données confidentielles. Les informations d'identification demandées par invite peuvent correspondre à un compte de domaine Windows ou une connexion de base de données. Si le serveur de base de données ne reconnaît pas les informations d'identification que vous fournissez, ou si l'utilisateur spécifié n'a pas reçu l'autorisation de récupérer les données, la connexion échoue.  
  
### <a name="no-credentials"></a>Aucune information d'identification  
 Aucune information d'identification n'est requise pour cette source de données. Pour exécuter ce rapport sur le serveur de rapports, le compte d'exécution sans assistance doit être configuré. Pour plus d’informations, consultez [configurer le compte d’exécution sans assistance &#40;Gestionnaire de Configuration de SSRS&#41; ](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) dans le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] documentation dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [la documentation en ligne](https://go.microsoft.com/fwlink/?linkid=121312).  
  
## <a name="see-also"></a>Voir aussi  
 [Installer, désinstaller et prise en charge du Générateur de rapports](../../2014/reporting-services/install-uninstall-and-report-builder-support.md)   
 [Connexions de données ou sources de données incorporées et partagées &#40;Générateur de rapports et SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [Boîte de dialogue, paramètres de Options de générateur de rapports &#40;Générateur de rapports&#41;](report-builder/set-default-options-for-report-builder.md)   
 [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Ajouter et vérifier une connexion de données ou d’une Source de données &#40;Générateur de rapports et SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
  
