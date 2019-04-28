---
title: Le compte d’exécution (Mode natif SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.executionaccount.F1
ms.assetid: 440b5a09-5fd4-4c3a-b510-f3c33cbf1c82
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9ba41b602ec91516e87b7fe5ec0276c586b17613
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62989040"
---
# <a name="execution-account-ssrs-native-mode"></a>Compte d'exécution (SSRS en mode natif)
  Utilisez cette page pour configurer un compte à utiliser pour le traitement sans assistance. Ce compte est utilisé dans des circonstances particulières lorsque d'autres sources d'informations d'identification ne sont pas disponibles :  
  
-   lorsque le serveur de rapports se connecte à une source de données qui n'exige pas d'informations d'identification ; les documents XML et certaines applications de base de données côté client sont des exemples de sources de données qui n'ont pas nécessairement besoin d'informations d'identification.  
  
-   lorsque le serveur de rapports se connecte à un autre serveur pour extraire des fichiers image externes ou d'autres ressources référencées dans un rapport.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif.  
  
 La définition de ce compte est facultative, mais si vous ne définissez pas le compte, l'utilisation des images externes et des connexions à certaines sources de données est limitée. Lorsque vous récupérez des fichiers image externes, le serveur de rapports vérifie si une connexion anonyme peut être établie. Si la connexion est protégée par mot de passe, le serveur de rapports utilise le compte de traitement sans assistance pour se connecter au serveur de rapports. Lors de l'extraction des données pour un rapport, le serveur de rapports emprunte l'identité de l'utilisateur actuel, invite l'utilisateur à fournir des informations d'identification, utilise des d'informations d'identification stockées ou utilise le compte de traitement sans assistance si la connexion de la source de données spécifie **Aucun** comme type d'informations d'identification. Le serveur de rapports n'autorise pas la délégation ou l'emprunt d'identité des informations d'identification de son compte de service lors de la connexion à d'autres ordinateurs. Par conséquent, il doit utiliser le compte de traitement sans assistance si aucune information d'identification n'est disponible.  
  
 Le compte que vous spécifiez doit être différent de celui utilisé pour exécuter le compte de service. Si vous configurez ce compte, il est stocké dans le fichier  RSReportServer.config sous forme de valeur chiffrée. Si vous exécutez le serveur de rapports dans un déploiement avec montée en puissance parallèle, vous devez configurer ce compte de la même façon sur chaque serveur de rapports.  
  
 Vous pouvez utiliser n'importe quel compte d'utilisateur Windows. Pour optimiser les résultats, choisissez un compte possédant des autorisations en lecture et des autorisations de connexion réseau afin de prendre en charge les connexions à d'autres ordinateurs. Il doit posséder des autorisations en lecture sur un fichier de données ou image externe que vous voulez utiliser dans un rapport. Ne spécifiez pas un compte local sauf si toutes les images externes et les sources de données de rapport sont stockées sur l'ordinateur du serveur de rapports. Utilisez le compte uniquement pour le traitement sans assistance des rapports.  
  
> [!NOTE]  
>  Si vous utilisez [!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)] with Advanced Services, vous devez simplement configurer ce compte si vous faites référence à des images externes dans un rapport et qu'une autorisation est requise pour accéder au fichier image. SQL Server Express ne prend pas en charge une connexion de source de données à un serveur distant. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473).  
  
 Pour ouvrir cette page, démarrez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et sélectionnez **Compte d'exécution** dans le volet de navigation. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Options  
 **Spécifier un compte d'exécution**  
 Sélectionnez un compte.  
  
 **Compte**  
 Entrez un compte d'utilisateur de domaine Windows. Utilisez le format suivant : *\<domaine>\\<compte_utilisateur\>*.  
  
 **Mot de passe**  
 Tapez le mot de passe.  
  
 **Confirmer le mot de passe**  
 Tapez de nouveau le mot de passe.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques d’aide F1 Gestionnaire de Configuration de Reporting Services &#40;SSRS en Mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Stocker des données chiffrées du serveur de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)  
  
  
