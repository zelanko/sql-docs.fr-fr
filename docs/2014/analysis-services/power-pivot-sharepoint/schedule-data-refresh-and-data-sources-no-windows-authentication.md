---
title: Actualisation planifiée des données et Sources de données qui ne prennent pas en charge l’authentification Windows (PowerPivot pour SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: d8d875bc-7823-46b7-a939-867cefd4de12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cf954178516cef633dbe34c1b8b01579c8f3e4ea
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62749052"
---
# <a name="schedule-data-refresh-and-data-sources-that-do-not-support-windows-authentication-powerpivot-for-sharepoint"></a>Actualisation planifiée des données et sources de données qui ne prennent pas en charge l'authentification Windows (PowerPivot pour SharePoint)
  Cette rubrique décrit un flux de travail d’actualisation planifiée des données PowerPivot pour SharePoint qui peut utiliser des sources de données qui **NE PRENNENT PAS EN CHARGE** l’authentification Windows. Par exemple, des sources de données Oracle ou IDM DB2. Les illustrations et les étapes figurant dans cette rubrique font référence à des sources de données Oracle, mais le même flux de travail s'applique aux autres sources de données.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2010 &#124; SharePoint 2013.|  
  
 **Vue d’ensemble :** Créez deux Store cible d’Applications sécurisées. Configurez la première application cible (PowerPivotDataRefresh) en vue d'utiliser les informations d'identification Windows. Configurez la deuxième application cible avec les informations d'identification d'une source de données qui ne prend pas en charge l'authentification Windows, une base de données Oracle par exemple. La deuxième application cible utilise également la première application cible pour le compte d'actualisation des données sans assistance.  
  
 ![as_powerpivot_refresh_no_windows_auth](../media/as-powerpivot-refresh-no-windows-auth.gif "as_powerpivot_refresh_no_windows_auth")  
  
-   **(1) PowerPivotDatarefresh :** Un Secure Store ID d’Application cible qui est défini avec l’authentification windows.  
  
-   **(2) OracleAuthentication :** Un Secure Store ID d’Application cible qui est défini avec les informations d’identification Oracle.  
  
-   **(3)**  Application du PowerPivot Service est configurée pour utiliser l’application cible « PowerPivotDataRefresh » pour le **compte d’actualisation des données sans assistance**.  
  
-   **(4)** Le classeur PowerPivot utilise des données Oracle. Les paramètres d’actualisation du classeur spécifient que la connexion de source de données utilise l’application cible **(2)** pour les informations d’identification.  
  
## <a name="prerequisites"></a>Prérequis  
  
-   Présence d'une application de service PowerPivot.  
  
-   Présence d'une application du service Banque d'informations sécurisées.  
  
-   Présence d'un classeur Excel avec un modèle de données PowerPivot.  
  
## <a name="to-create-a-target-application-id-that-uses-windows-authentication"></a>Pour créer un ID d'application cible qui utilise l'authentification Windows  
  
1.  Dans l'administration centrale de SharePoint, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur le nom de votre application de service Banque d'informations sécurisées.  
  
3.  Sur la page **Gérer** , cliquez sur **Nouveau**. ![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application")  
  
4.  Sur la page **Créer une nouvelle application cible du magasin sécurisé** , configurez les valeurs suivantes :  
  
    -   **ID d’Application cible :** PowerPivotDataRefresh.  
  
    -   **Nom complet :** PowerPivotDataRefresh.  
  
    -   **Adresse de messagerie du contact :** ?  
  
    -   **Type d’Application cible :** groupe.  
  
    -   **URL de Page d’Application cible :** Aucun.  
  
5.  Cliquer sur **Suivant**.  
  
6.  Sur la page Informations d'identification, ne changez pas les deux noms de champ par défaut, ainsi que les types de champ pour **Nom d'utilisateur Windows** et **Mot de passe Windows**.  
  
7.  Cliquer sur **Suivant**.  
  
8.  Sur la page **Paramètres d'appartenance** , ajoutez au moins un **administrateur d'application cible** , puis ajoutez des membres qui ont besoin d'accéder à l'application cible.  
  
9. Cliquez sur **OK**.  
  
10. Le nouvel ID d'application cible est ajouté à la liste. Sélectionnez l’ID d’application cible et cliquez sur **définir les informations d’identification**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key").  
  
11. Tapez le Nom d'utilisateur Windows et le Mot de passe Windows, puis cliquez sur **OK**.  
  
## <a name="to-create-a-target-application-id-that-uses-oracle-credentials"></a>Pour créer un ID d'application cible qui utilise les informations d'identification Oracle  
  
1.  Dans l'administration centrale de SharePoint, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur le nom de votre application de service Banque d'informations sécurisées.  
  
3.  Sur le **gérer** , cliquez sur **New**![as_powerpivot_refresh_sss_new_target_application](../media/as-powerpivot-refresh-sss-new-target-application.gif "as_powerpivot_refresh_sss_new_target_application ").  
  
4.  Sur la page **Créer une nouvelle application cible du magasin sécurisé** , configurez les valeurs suivantes :  
  
    -   **ID d’Application cible :** OracleAuthentication.  
  
    -   **Nom complet :** OracleAuthentication.  
  
    -   **Adresse de messagerie du contact :** ?  
  
    -   **Type d’Application cible :** groupe.  
  
    -   **URL de Page d’Application cible :** Aucun.  
  
5.  Cliquer sur **Suivant**.  
  
6.  Sur le **informations d’identification** , changez le nom du premier champ à `Oracle User ID` et modifiez le **Type de champ** à `User Name`.  
  
     Modifier le nom du deuxième champ à `Oracle Password` et **Type de champ** à `Password`.  
  
7.  Cliquer sur **Suivant**.  
  
8.  Sur la page **Paramètres d'appartenance** , ajoutez au moins un **administrateur d'application cible** , puis ajoutez des membres qui ont besoin d'accéder à l'application cible.  
  
9. Cliquez sur **OK**.  
  
10. Le nouvel ID d'application cible est ajouté à la liste. Sélectionnez l’ID d’application cible et cliquez sur **définir les informations d’identification**![as_powerpivot_refresh_sss_set_key](../media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key").  
  
11. Tapez l'ID d'utilisateur Oracle, ainsi que le mot de passe Oracle, puis cliquez sur **OK**.  
  
 Pour plus d’informations, consultez la section « Pour créer une application cible pour l’authentification SQL Server » dans [utilisez Secure Store avec l’authentification SQL Server (SharePoint Server 2013)](https://technet.microsoft.com/library/gg298949.aspx) (https://technet.microsoft.com/library/gg298949.aspx).  
  
## <a name="to-configure-the-powerpivot-service-application"></a>Pour configurer l'application de service PowerPivot  
  
1.  Dans l'administration centrale de SharePoint, cliquez sur Gérer les applications de service.  
  
2.  Cliquez sur le nom de votre Application de Service PowerPivot, par exemple « par défaut PowerPivot Service Application ».  
  
3.  Cliquez sur **Configurer les paramètres d'application de service** dans la section Actions.  
  
4.  Dans le **d’actualisation des données** section, définissez le **compte PowerPivot sans assistance données Actualiser**à`PowerPivotDataRefresh` puis cliquez sur **OK**.  
  
     ![as_powerpivot_refresh_new_refresh_acount](../media/as-powerpivot-refresh-new-refresh-acount.gif "as_powerpivot_refresh_new_refresh_acount")  
  
## <a name="to-configure-the-workbook"></a>Pour configurer le classeur  
  
1.  Accédez à votre classeur dans la galerie PowerPivot et cliquez sur **gérer l’actualisation des données**![as_powerpivot_refresh_manage_reresh](../media/as-powerpivot-refresh-manage-reresh.gif "as_powerpivot_refresh_manage_reresh").  
  
2.  Si la page **Historique d'actualisation des données** s'affiche, cliquez sur **Configurer la planification**.  
  
3.  Cliquez sur **Activer**.  
  
4.  Cliquez sur **Aussi actualiser dès que possible**.  
  
5.  Dans la section **Informations d'identification** , cliquez sur **Utilisez le compte d'actualisation des données configuré par l'administrateur**.  
  
6.  Désactivez la case **Toutes les sources de données**.  
  
7.  Sélectionnez **Actualiser** pour la source de données qui utilise les données Oracle. Le nom de la source de données peut être modifié dans Microsoft Excel dans le menu **Données**, **Connexions**, **Propriétés** .  
  
8.  Sous votre source de données, sélectionnez **Utiliser la planification par défaut**.  
  
9. Sélectionnez **Connectez-vous à l'aide des informations d'identification enregistrées dans le service Banque d'informations sécurisé (SSS) pour la connexion à la source de données. Entrez l’ID utilisé pour consulter les informations d’identification dans la zone Identification SSS**.  
  
10. Dans le **ID :** , tapez `OracleAuthentication`.  
  
11. Cliquez sur **OK**.  
  
     Si un message d'erreur semblable au suivant s'affiche : `The provided Secure Store target application is either incorrectly configured or does not exist`.  
  
     Les deux solutions courantes sont les suivantes :  
  
    -   Vérifiez que l'ID d'application cible est correct.  
  
    -   Vérifiez que vous définissez les informations d'identification pour l'application cible.  
  
## <a name="to-verify-data-refresh-with-the-new-authentication"></a>Pour vérifier l'actualisation des données avec la nouvelle authentification  
 Lorsque vous cliquez sur **OK**, la page **Historique d'actualisation** s'affiche. Après quelques minutes, vous devez voir apparaître un nouvel élément dans l'historique d'actualisation du fait que vous avez sélectionné **Aussi actualiser dès que possible**dans les étapes précédentes. La valeur par défaut du travail du minuteur **Travail du minuteur d’actualisation des données PowerPivot** est de 1 minute. Si aucun nouvel élément n'apparaît dans l'historique d'actualisation, patientez quelques minutes, puis actualisez votre navigateur. Si le problème persiste, vérifiez la valeur actuelle du travail du minuteur.  
  
## <a name="more-information"></a>Informations supplémentaires  
  
-   [Configurer le service Banque d'informations sécurisé dans SharePoint 2013](https://technet.microsoft.com/library/ee806866.aspx).  
  
-   Consultez la section « Actualisation planifiée des données » de [d’actualisation des données PowerPivot avec SharePoint 2013 et SQL Server 2012 SP1 (Analysis Services)](https://msdn.microsoft.com/library/jj879294.aspx#bkmk_windows_auth_interactive_data_refresh).  
  
  
