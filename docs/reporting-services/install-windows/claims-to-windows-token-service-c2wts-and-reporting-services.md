---
title: "Revendications au Service d’émission de jeton Windows (c2WTS) et Reporting Services | Documents Microsoft"
ms.custom: The Claims to Windows Token Service (C2WTS) is used by SharePoint and needs to be configured for Kerberos constrained delegation to work with SQL Server Reporting Services properly.
ms.date: 09/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: a9397f427cac18d0c8bfc663f6bd477b0440b8a3
ms.openlocfilehash: 8a478bba3cde66967594d5ef02f867de5b33edd7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/15/2017

---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Service d'émission de jetons Revendications vers Windows (C2WTS) et Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)])

Les revendications SharePoint vers Windows Token Service (C2WTS) est requises si vous souhaitez afficher des rapports en mode natif dans le [composant WebPart Visionneuse de rapports SQL Server Reporting Services](../report-server-sharepoint/deploy-report-viewer-web-part.md).

C2WTS est également nécessaire avec SQL Server Reporting Services SharePoint mode si vous souhaitez utiliser l’authentification Windows pour les sources de données qui sont en dehors de la batterie de serveurs SharePoint. C2WTS est nécessaire même si vos sources de données sont sur le même ordinateur que le service partagé. Toutefois dans ce scénario, la délégation contrainte n'est pas nécessaire.

> [!NOTE]
> Intégration de Reporting Services avec SharePoint n’est plus disponible après SQL Server 2016.

## <a name="report-viewer-web-part-configuration"></a>Configuration du composant WebPart Report Viewer

Le composant WebPart Visionneuse de rapports peut être utilisé pour incorporer des rapports en mode natif de SQL Server Reporting Services au sein de votre site SharePoint. Ce composant WebPart n’est disponible pour SharePoint 2013 et SharePoint 2016. Assurez-vous de SharePoint 2013 et SharePoint 2016 utilisent l’authentification par revendications. SQL Server Reporting Services (mode natif) utilise l’authentification Windows par défaut. Par conséquent, C2WTS doit être configuré correctement pour les rapports afficher correctement.

## <a name="sharepoint-mode-integaration"></a>Integaration du mode SharePoint

**Cette section s’applique uniquement à SQL Server 2016 Reporting Services et les versions antérieures.**

Les revendications SharePoint vers Windows Token Service (C2WTS) est requises avec SQL Server Reporting Services SharePoint mode si vous souhaitez utiliser l’authentification Windows pour les sources de données qui sont en dehors de la batterie de serveurs SharePoint. Cela est vrai même si l’utilisateur accède aux sources de données avec l’authentification Windows, car la communication entre le serveur web frontal (WFE) et le service partagé Reporting Services sera toujours l’authentification par revendications.

## <a name="steps-needed-to-configure-c2wts"></a>Étapes nécessaires pour configurer c2WTS

Les jetons créés par C2WTS fonctionnent uniquement avec la délégation contrainte (contraint à des services spécifiques) et l'option de configuration « Utiliser tout protocole d'authentification ». Comme indiqué précédemment, si vos sources de données sont sur le même ordinateur que le service partagé, la délégation contrainte n'est pas nécessaire.

Si votre environnement utilise la délégation contrainte Kerberos, le service SharePoint server et les sources de données externes doivent résider dans le même domaine Windows. Tout service qui s’appuie sur le service d’émission de jetons Revendications vers Windows (C2WTS) doit utiliser la délégation **contrainte** Kerberos pour permettre à C2WTS d’utiliser une transition de protocole Kerberos dans la conversion de revendications en informations d’identification Windows. Ces exigences s'appliquent à tous les services partagés SharePoint. Pour plus d’informations, consultez [Planifier l’authentification Kerberos dans SharePoint 2013](http://technet.microsoft.com/library/ee806870.aspx).  

1. Configurer le compte de service C2WTS. Ajoutez le compte de service au groupe Administrateurs local sur chaque serveur que C2WTS sera utilisé.

    Pour le **composant WebPart Visionneuse de rapports**, il s’agit des serveurs Web frontaux (WFE). Pour **en mode intégré SharePoint**, il s’agit des serveurs d’applications dans lequel le service Reporting Services est en cours d’exécution.

2. Configurer la délégation pour le compte de service C2WTS.

    Le compte doit la délégation contrainte avec transition de protocole et les autorisations de déléguer aux services qu’il est nécessaire pour communiquer avec (autrement dit, SQL Server Database Engine, SQL Server Analysis Services). Pour configurer la délégation, vous pouvez utiliser le composant logiciel enfichable utilisateurs Active Directory et l’ordinateur et devez être un administrateur de domaine.

    > [!IMPORTANT]
    > Les paramètres vous configurez pour le compte de service C2WTS, sous l’onglet Délégation, doit correspondre au compte de service principal utilisé. Pour le **composant WebPart Visionneuse de rapports**, ce sera le compte de service pour l’application web SharePoint. Pour **en mode intégré SharePoint**, il s’agit du compte de service Reporting Services.
    >
    > Par exemple, si vous autorisez le compte de service C2WTS à déléguer à un Service SQL, vous devez faire de même sur le compte de service Reporting Services en mode intégré SharePoint.

    * Cliquez avec le bouton droit sur chaque compte de service et ouvrez la boîte de dialogue des propriétés. Dans la boîte de dialogue, cliquez sur l'onglet **Délégation** .

        L’onglet délégation n’est visible si l’objet a un nom de principal du Service (SPN) qui lui est affecté. C2WTS ne nécessite pas de SPN sur le compte C2WTS, toutefois, sans SPN, le **délégation** onglet ne seront pas visible. Une autre façon de configurer la délégation contrainte consiste à utiliser un utilitaire tel que **ADSIEdit**.

    * Les options de configuration principales dans l'onglet Délégation sont les suivantes :

        * Sélectionnez **n’approuver cet utilisateur pour la délégation aux services spécifiés uniquement**
        * Sélectionnez **utiliser tout protocole d’authentification**

    * Sélectionnez **Ajouter** pour ajouter un service auquel déléguer.

    * Sélectionnez **utilisateurs ou ordinateurs...** * et entrez le compte qui héberge le service. Par exemple, si un serveur SQL Server s’exécute sous un compte nommé *sqlservice*, entrez `sqlservice`. 

    * Sélectionnez la liste des services. Les SPN disponibles sur ce compte s’affichent. Si vous ne voyez pas le service sur ce compte, il est peut-être manquant ou placé sur un autre compte. Vous pouvez utiliser l’utilitaire SetSPN pour ajuster les SPN.

    * Cliquez sur OK pour fermer les boîtes de dialogue.

3. Configurer C2WTS *AllowedCallers*.

    C2WTS requiert que les identités 'appelants' explicitement répertoriées dans le fichier de configuration **C2WTShost.exe.config**. C2WTS n'accepte pas de demandes de tous les utilisateurs authentifiés dans le système, sauf s'il est configuré pour cela. Dans ce cas, le « appelant » est le groupe Windows WSS_WPG. Le fichier C2WTShost.exe.confi est enregistré à l’emplacement suivant :

    La modification du compte de service dans l’Administration centrale de SharePoint, pour le service C2WTS, ajoute ce compte au groupe WSS_WPG.

    **\Program Files\Windows Identity Foundation\v3.5\c2WTShost.exe.config**

    L'exemple suivant montre le fichier de configuration :

    ```
    <configuration>
      <windowsTokenService>
        <!--  
            By default no callers are allowed to use the Windows Identity Foundation Claims To NT Token Service.  
            Add the identities you wish to allow below.  
          -->
        <allowedCallers>
          <clear/>
          <add value="WSS_WPG" />
        </allowedCallers>
      </windowsTokenService>
    </configuration>
    ```

4. Démarrez les revendications vers Windows Token Service via l’Administration centrale de SharePoint sur le **gérer les Services sur le serveur** page. Le service doit être démarré sur le serveur qui effectuera l'action. Par exemple, si vous avez un serveur qui est un serveur Web frontal et un autre serveur est un serveur d’applications qui possède le service partagé de SQL Server Reporting Services en cours d’exécution, seulement vous devront démarrer C2WTS sur le serveur d’applications. C2WTS est nécessaire uniquement sur un serveur Web frontal, si vous utilisez le composant WebPart Visionneuse de rapports.

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

