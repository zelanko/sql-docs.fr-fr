---
title: Configurer une authentification de base sur le serveur de rapports | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, configuration
- Basic authentication
ms.assetid: 8faf2938-b71b-4e61-a172-46da2209ff55
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 32b46265b5da376bc974b55c48bf54bad88917d8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66102160"
---
# <a name="configure-basic-authentication-on-the-report-server"></a>Configurer l’authentification de base sur le serveur de rapports
  Par défaut, Reporting Services accepte les demandes qui spécifient l'authentification Negotiate et NTLM. Si votre déploiement inclut des applications clientes ou des navigateurs qui utilisent l'authentification de base, vous devez l'ajouter à la liste des types pris en charge. De plus, si vous voulez utiliser le Générateur de rapports, vous devez activer l'accès anonyme aux fichiers Générateur de rapports.  
  
 Pour configurer l'authentification de base sur le serveur de rapports, modifiez les éléments et les valeurs XML dans le fichier RSReportServer.config. Vous pouvez copier et coller les exemples de cette rubrique pour remplacer les valeurs par défaut.  
  
 Avant d'activer l'authentification de base, vérifiez que votre infrastructure de sécurité la prend en charge. Sous l'authentification de base, le service Web Report Server passe des informations d'identification à l'autorité de sécurité locale. Si ces informations spécifient un compte d'utilisateur local, l'utilisateur est authentifié par l'autorité de sécurité locale sur le serveur de rapports et l'utilisateur obtient un jeton de sécurité qui est valide pour les ressources locales. Les informations d'identification pour les comptes d'utilisateur de domaine sont transférées et sont authentifiées par un contrôleur de domaine. Le ticket résultant est valide pour les ressources réseau.  
  
 Le chiffrement du canal, tel que SSL (Secure Sockets Layer), est requis si vous souhaitez réduire le risque d'interception des informations d'identification lors de leur transit vers un contrôleur de domaine sur votre réseau. L'authentification de base transmet en texte en clair le nom d'utilisateur et le mot de passe en encodage base 64. L'ajout du chiffrement de canal rend le paquet illisible. Pour plus d’informations, consultez [Configurer des connexions SSL sur un serveur de rapports en mode natif](configure-ssl-connections-on-a-native-mode-report-server.md).  
  
 Après avoir activé l'authentification de base, n'oubliez pas que les utilisateurs ne peuvent pas sélectionner l'option **Sécurité intégrée de Windows** lors de la définition de propriétés de connexion sur une source de données externe qui fournit des données à un rapport. L'option est grisée dans les pages de propriétés de source de données.  
  
> [!NOTE]  
>  Les instructions suivantes sont destinées à un serveur de rapports en mode natif. Si le serveur de rapports est déployé en mode intégré SharePoint, vous devez utiliser les paramètres d'authentification par défaut qui spécifient la sécurité intégrée de Windows. Le serveur de rapports utilise des fonctionnalités internes dans l'extension d'authentification Windows par défaut pour prendre en charge le serveur de rapports en mode intégré SharePoint.  
  
### <a name="to-configure-a-report-server-to-use-basic-authentication"></a>Pour configurer un serveur de rapports pour utiliser l'authentification de base  
  
1.  Ouvrez RSReportServer.config dans un éditeur de texte.  
  
     Le fichier se trouve dans  *\<lecteur > :* \Program Files\Microsoft SQL Server\MSRS12. MSSQLSERVER\Reporting Services\ReportServer.  
  
2.  Trouver <`Authentication`>.  
  
3.  Copiez, parmi les structures XML suivantes, celle qui répond le mieux à vos besoins. La première structure XML fournit des espaces réservés pour spécifier tous les éléments décrits dans la section suivante :  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <RSWindowsBasic>  
                       <LogonMethod>3</LogonMethod>  
                       <Realm></Realm>  
                       <DefaultDomain></DefaultDomain>  
                 </RSWindowsBasic>  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
     Si vous utilisez des valeurs par défaut, vous pouvez copier la structure de l'élément minimale :  
  
    ```  
          <AuthenticationTypes>  
                 <RSWindowsBasic/>  
          </AuthenticationTypes>  
    ```  
  
4.  Collez-la sur les entrées existantes de <`Authentication`>.  
  
     Si vous utilisez plusieurs types d'authentification, ajoutez juste l'élément `RSWindowsBasic` mais ne supprimez pas les entrées pour `RSWindowsNegotiate`, `RSWindowsNTLM` ou `RSWindowsKerberos`.  
  
     Pour prendre en charge le navigateur Safari, vous ne pouvez pas configurer le serveur de rapports pour utiliser plusieurs types d'authentification. Vous devez spécifier `RSWindowsBasic` uniquement et supprimer les autres entrées.  
  
     Notez que vous ne pouvez pas utiliser `Custom` avec d'autres types d'authentification.  
  
5.  Remplacez les valeurs vides pour <`Realm`> ou <`DefaultDomain`> avec des valeurs qui sont valides pour votre environnement.  
  
6.  Enregistrez le fichier.  
  
7.  Si vous avez configuré un déploiement avec montée en puissance parallèle, répétez ces étapes pour d'autres serveurs de rapports du déploiement.  
  
8.  Redémarrez le serveur de rapports pour effacer toutes les sessions qui sont actuellement ouvertes.  
  
## <a name="rswindowsbasic-reference"></a>Référence RSWindowsBasic  
 Les éléments suivants peuvent être spécifiés lors de la configuration de l'authentification de base.  
  
|Élément|Requis|Valeurs valides|  
|-------------|--------------|------------------|  
|LogonMethod|Oui<br /><br /> Si vous ne spécifiez pas de valeur, 3 est utilisé.|`2` = ouverture de session réseau, destinée aux serveurs hautes performances pour l’authentification des mots de passe en texte brut.<br /><br /> `3` = ouverture de session basée sur du texte en clair ; les informations d’identification d’ouverture de session sont conservées dans le package d’authentification envoyé avec chaque requête HTTP, ce qui permet au serveur d’emprunter l’identité de l’utilisateur lors de la connexion à d’autres serveurs du réseau. (Par défaut)<br /><br /> Remarque : Les valeurs 0 (pour l’ouverture de session interactive) et 1 (pour l’ouverture de session de lot) ne sont pas pris en charge dans [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)].|  
|Realm|Ce paramètre est facultatif|Spécifie une partition de ressource qui inclut les fonctionnalités d'autorisation et d'authentification permettant de contrôler l'accès aux ressources protégées de votre organisation.|  
|DefaultDomain|Ce paramètre est facultatif|Spécifie le domaine utilisé par le serveur pour authentifier l'utilisateur. Cette valeur est facultative, mais si vous l'omettez, le serveur de rapports utilise le nom d'ordinateur comme domaine. Si l'ordinateur est membre du domaine, ce domaine est le domaine par défaut. Si vous avez installé le serveur de rapports sur un contrôleur de domaine, le domaine utilisé est celui contrôlé par l'ordinateur.|  
  
## <a name="enabling-anonymous-access-to-report-builder-application-files"></a>Activation de l'accès anonyme aux fichiers d'application du Générateur de rapports  
 Le Générateur de rapports utilise la technologie ClickOnce pour télécharger et installer les fichiers d'application sur l'ordinateur client. Lorsqu'il démarre sur l'ordinateur client, le lanceur d'applications ClickOnce fait une demande des fichiers d'application supplémentaires sur le serveur de rapports. Si le serveur de rapports est configuré pour l'authentification de base, le contrôle d'authentification du lanceur d'applications ClickOnce échoue car il ne prend pas en charge ce type d'authentification.  
  
 Pour contourner ce problème, configurez l'accès anonyme aux fichiers programme du Générateur de rapports. De cette manière, ClickOnce ignore le contrôle d'authentification au moment d'extraire ses fichiers. Pour activer l'accès anonyme, procédez comme suit :  
  
-   Vérifiez que le serveur de rapports est configuré pour l'authentification de base.  
  
-   Créez un dossier Bin sous ReportBuilder et copiez quatre assemblys dans le dossier.  
  
-   Ajoutez l'élément `IsReportBuilderAnonymousAccessEnabled` à RSReportServer.config et affectez-lui la valeur `True`. Une fois le fichier enregistré, le serveur de rapports crée un nouveau point de terminaison pour le Générateur de rapports. Le point de terminaison est utilisé en interne pour accéder aux fichiers programme et ne contient pas d'interface de programmation que vous pouvez utiliser dans le code. Avoir un point de terminaison séparé permet au Générateur de rapports de s'exécuter dans son propre domaine d'application dans la limite du processus du service Report Server.  
  
-   Vous pouvez éventuellement spécifier un compte de privilèges minimaux pour traiter les demandes sous un contexte de sécurité différent du serveur de rapports. Ce compte devient le compte anonyme pour accéder aux fichiers Générateur de rapports sur un serveur de rapports. Le compte définit l'identité du thread dans le processus de travail ASP.NET. Les demandes qui s'exécutent dans ce thread sont passées au serveur de rapports sans contrôle d'authentification. Ce compte est équivalent à IUSR_\<machine > compte dans Internet Information Services (IIS), qui est utilisé pour définir le contexte de sécurité pour les processus de travail ASP.NET traite lorsque l’accès anonyme et l’emprunt d’identité sont activés. Pour spécifier le compte, ajoutez-le à un fichier Web.config du Générateur de rapports.  
  
 Le serveur de rapports doit être configuré pour l'authentification de base pour activer l'accès anonyme aux fichiers programme du Générateur de rapports. Si le serveur de rapports n’est pas configuré pour l'authentification de base, un message d'erreur s'affichera lorsque vous tenterez d'activer l'accès anonyme.  
  
 Pour plus d’informations sur les problèmes d’authentification et le Générateur de rapports, consultez [Configurer l’accès au Générateur de rapports](../report-server/configure-report-builder-access.md).  
  
#### <a name="to-configure-report-builder-access-on-a-report-server-configured-for-basic-authentication"></a>Pour configurer l'accès au Générateur de rapports sur un serveur de rapports configuré pour l'authentification de base  
  
1.  Vérifiez que le serveur de rapports est configuré pour l'authentification de base en activant les paramètres d'authentification dans le fichier RSReportServer.config.  
  
2.  Créez un dossier BIN sous le dossier ReportBuilder. Par défaut, ce dossier se trouve sous \Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\ReportServer\ReportBuilder.  
  
3.  Copiez les assemblys suivants à partir du dossier ReportServer\Bin dans le dossier ReportBuilder\BIN :  
  
     Microsoft.ReportingServices.Diagnostics.dll  
  
     Microsoft.ReportingServices.Interfaces.dll  
  
     ReportingServicesAppDomainManager.dll  
  
     RSHttpRuntime.dll  
  
4.  Créez éventuellement un fichier Web.config pour traiter des demandes du Générateur de rapports sous un compte Anonyme :  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
    <system.web>  
    <authentication mode="Windows" />    
    <identity impersonate="true " userName="username" password="password"/>  
    </system.web>  
    </configuration>  
    ```  
  
     Le mode d’authentification doit avoir la valeur `Windows` si vous incluez un fichier Web.config.  
  
     `Identity impersonate` peut avoir la valeur `True` ou `False`.  
  
    -   Affectez-lui la valeur `False` pour qu'ASP.NET ne lise pas le jeton de sécurité. La demande s'exécute dans le contexte de sécurité du service Report Server.  
  
    -   Affectez-lui la valeur `True` pour qu'ASP.NET lise le jeton de sécurité de la couche hôte. Si vous lui affectez la valeur `True`, vous devez également spécifier `userName` et `password` pour désigner un compte anonyme. Les informations d'identification que vous spécifiez déterminent le contexte de sécurité sous lequel la demande est émise.  
  
5.  Enregistrez le fichier Web.config dans le dossier ReportBuilder\bin.  
  
6.  Ouvrez le fichier RSReportServer.config, dans la section Services, recherchez `IsReportManagerEnabled` et ajoutez en dessous le paramètre suivant :  
  
    ```  
    <IsReportBuilderAnonymousAccessEnabled>True</IsReportBuilderAnonymousAccessEnabled>  
    ```  
  
7.  Enregistrez le fichier RSReportServer.config et fermez-le.  
  
8.  Redémarrez le serveur de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Domaines d'application des applications du serveur de rapports](../report-server/application-domains-for-report-server-applications.md)   
 [Sécurité et protection de Reporting Services](reporting-services-security-and-protection.md)  
  
  
