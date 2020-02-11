---
title: Configurer les informations d’identification stockées pour l’actualisation des données PowerPivot (PowerPivot pour SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 987eff0f-bcfe-4bbd-81e0-9aca993a2a75
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 23f35c8998b204182f25f85f8f7694fb60d042b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087458"
---
# <a name="configure-stored-credentials-for-powerpivot-data-refresh-powerpivot-for-sharepoint"></a>Configurer les informations d'identification stockées pour l'actualisation des données PowerPivot (PowerPivot pour SharePoint)
  Les travaux d'actualisation des données PowerPivot peuvent s'exécuter sous n'importe quel compte d'utilisateur Windows, du moment que vous créez une application cible dans le service Banque d'informations sécurisé pour stocker les informations d'identification que vous souhaitez utiliser. De la même façon, si vous souhaitez fournir une connexion à une base de données qui varie de celle utilisée à l'origine pour importer les données dans PowerPivot pour Excel, vous pouvez mapper ces informations d'identification à une application cible de service Banque d'informations sécurisé, puis spécifier cette application cible dans une planification d'actualisation des données.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010  
  
 Après avoir suivi les instructions de cette rubrique, vous serez en mesure d'utiliser l'option d'informations d'identification suivante dans la page de planification de l'actualisation des données PowerPivot :  
  
 ![SSAS_PowerPivotDataRefreshCreds_Stored](media/ssas-powerpivotdatarefreshcreds-stored.gif "SSAS_PowerPivotDataRefreshCreds_Stored")  
  
 Cette rubrique explique comment configurer les noms d'utilisateur et les mots de passe servant à actualiser les données PowerPivot dans une batterie de serveurs SharePoint 2010. Pour exécuter ces étapes, le service Banque d'informations sécurisé doit avoir été activé et une clé principale générée. Pour plus d’informations, consultez [actualisation des données PowerPivot avec SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)  
  
 Cette rubrique contient les sections suivantes :  
  
 [Configurer un compte Windows pour l'actualisation des données](#configAny)  
  
 [Configurer un compte prédéfini pour l'accès aux sources de données externes ou tierces](#config3rd)  
  
 Si vous rencontrez des problèmes lors de la configuration ou de l’utilisation de l’actualisation des données, consultez la page [résolution des problèmes d’actualisation des données PowerPivot](https://go.microsoft.com/fwlink/?LinkID=223279) sur le wiki TechNet pour les solutions possibles.  
  
##  <a name="configAny"></a>Configurer un compte Windows pour l’actualisation des données  
 Lorsqu'un utilisateur SharePoint définit une planification d'actualisation des données, il doit spécifier l'identité de l'utilisateur sous laquelle l'actualisation des données est effectuée. Les options incluent la sélection du compte d'actualisation des données PowerPivot sans assistance, l'entrée de son compte d'utilisateur de domaine Windows ou la saisie d'un autre compte d'utilisateur Windows valide pour l'actualisation des données. Les étapes de cette section concernent la dernière option : la spécification d'un autre compte Windows.  
  
 Vous pouvez choisir cette approche si vous souhaitez une alternative à l'utilisation du compte d'actualisation des données PowerPivot sans assistance (disponible pour tous les utilisateurs PowerPivot sur SharePoint) ou des informations d'identification du propriétaire du classeur. Par exemple, vous pouvez mettre une série de comptes d'actualisation des données à disposition de différents groupes de travail pour vous aider à suivre et à gérer l'activité d'actualisation des données au niveau de l'organisation.  
  
> [!IMPORTANT]  
>  Les personnes et les applications qui utilisent cette application cible (et les informations d'identification qu'elle stocke) doivent être répertoriées comme membres de l'application. Vous devez ajouter l'identité de chaque application de service PowerPivot qui utilisera l'application cible, votre compte Windows et les comptes de groupes ou d'utilisateurs des personnes qui spécifieront cette application cible dans leurs planifications d'actualisation des données. Vous pouvez spécifier tous ces comptes lorsque vous créez l'application cible. Si vous ne connaissez pas tous les comptes de groupes et d'utilisateurs qui auront besoin de l'accès à cette application, vous pouvez les ajouter ultérieurement une fois l'application cible créée.  
  
 La configuration des informations d'identification stockées pour l'actualisation des données s'effectue en quatre étapes :  
  
-   Créez l'application cible qui stocke les informations d'identification.  
  
-   Accordez des autorisations Collaboration au compte.  
  
-   Accordez des autorisations de lecture sur le compte pour accéder aux sources de données externes pendant l'actualisation des données.  
  
-   Vérifiez que l'actualisation des données fonctionne lorsque vous spécifiez cette application cible dans une planification d'actualisation des données.  
  
### <a name="step-1-create-a-target-application"></a>Étape 1 : créer une application cible  
  
1.  Dans administration centrale, dans gestion des applications, cliquez sur **gérer les applications de service**.  
  
2.  Cliquez sur **service Banque d’informations sécurisé**.  
  
3.  Dans gérer les applications cibles, cliquez sur **nouveau**.  
  
4.  Dans ID d'application cible, tapez une chaîne de texte. La chaîne doit être unique, mais également facile à mémoriser. Les utilisateurs tapent cette chaîne dans les pages de planification de l'actualisation des données à chaque fois qu'ils veulent utiliser les informations d'identification stockées dans cette application.  
  
5.  Dans Nom complet, entrez un nom descriptif. Ce nom est utilisé uniquement à des fins d'affichage. Il n'est pas utilisé pour spécifier l'application cible dans une planification d'actualisation des données.  
  
6.  Dans Adresse de messagerie du contact, tapez votre adresse de messagerie.  
  
7.  Dans type d’application cible, sélectionnez **groupe**.  
  
    > [!IMPORTANT]  
    >  Le choix d'un type de compte de groupe est nécessaire, car il vous permet de spécifier tous les comptes de service et d'utilisateur qui demandent l'accès aux informations d'identification. Pour chaque demande, le service système PowerPivot vérifie si le demandeur est membre de l'application cible.  
  
8.  Ignorez l'URL de la page de l'application cible. L'actualisation des données PowerPivot ne l'utilise pas.  
  
9. Cliquez sur **Suivant**.  
  
10. Dans la page **spécifier les champs d’informations d’identification pour votre application cible de banque d’informations sécurisée** , acceptez les valeurs par défaut. Les noms et les types de champ doivent être le nom d’utilisateur Windows et le mot de passe Windows.  
  
11. Cliquez sur Suivant.  
  
12. Dans Administrateurs d'applications cibles, spécifiez les comptes d'utilisateurs de domaine Windows des utilisateurs SharePoint qui bénéficient d'un accès administrateur aux paramètres des applications cibles (par exemple, la capacité d'ajouter ou de supprimer des comptes dans la liste Membres).  
  
13. Dans Membres, ajoutez les comptes de groupes et d'utilisateurs suivants :  
  
    1.  En tant que créateur de l'application, ajoutez votre compte d'utilisateur Windows à la liste Membres.  
  
    2.  Ajoutez l'identité du pool d'applications de l'application de service PowerPivot afin qu'elle puisse récupérer les informations d'identification lors de la planification de l'exécution de l'actualisation des données. Pour afficher l’identité du pool d’applications, accédez à **gérer les applications de service**, sélectionnez l’application de service PowerPivot en cliquant sur l’espace vide en regard du nom (cela sélectionne la ligne), puis cliquez sur **Propriétés**. Le compte de sécurité qui apparaît dans cette page est le compte à ajouter comme membre de l'application cible.  
  
    3.  Ajoutez les comptes d'utilisateur et de groupe Windows qui seront inclus dans cette application cible dans les planifications d'actualisation des données.  
  
14. Cliquez sur **OK**.  
  
15. Sélectionnez l’application cible que vous venez de créer, cliquez sur la flèche orientée vers le bas et sélectionnez **définir les informations d’identification.**  
  
16. Dans Propriétaire des informations d'identification, notez que la liste de propriétaires d'informations d'identification est en lecture seule. Les comptes propriétaires des informations d'identification sont membres de l'application cible. Pour ajouter ou supprimer un propriétaire d'informations d'identification, vous devez ajouter ou supprimer des comptes dans la liste de membres de l'application cible.  
  
     Dans Nom d'utilisateur Windows et Mot de passe Windows, tapez les informations d'identification du compte d'utilisateur Windows qui sera utilisé pour exécuter l'actualisation des données.  
  
17. Cliquez sur **OK**.  
  
###  <a name="bkmk_grant"></a>Étape 2 : accorder des autorisations collaboration au compte  
 Avant de pouvoir utiliser les informations d'identification stockées, il faut attribuer au compte des autorisations Collaboration sur tous les classeurs PowerPivot pour lesquels il est utilisé. Ce niveau d'autorisation est nécessaire pour ouvrir le classeur d'une bibliothèque, puis l'enregistrer à nouveau dans la bibliothèque une fois les données actualisées.  
  
 L'affectation d'autorisations est une procédure effectuée par l'administrateur de collection de sites. Les autorisations SharePoint peuvent être affectées à la collection de sites racine ou à n'importe quel niveau inférieur, notamment aux documents individuels et aux éléments. La manière dont vous définissez les autorisations dépendra du degré de granularité que vous souhaitez. Les étapes suivantes vous montrent une méthode d'affectation des autorisations.  
  
1.  Sur un site SharePoint, dans actions du site, cliquez sur **autorisations du site**.  
  
2.  Cliquez sur **Accorder des autorisations**.  
  
3.  Dans Sélectionnez les utilisateurs, tapez le nom du compte d'utilisateur de domaine Windows que vous avez spécifié dans l'application cible.  
  
4.  Dans accorder des autorisations, sélectionnez **accorder directement les**autorisations des utilisateurs.  
  
5.  Sélectionnez **collaboration**, puis cliquez sur **OK**.  
  
###  <a name="bkmk_dbread"></a>Étape 3 : accorder des autorisations de lecture pour accéder aux sources de données externes utilisées dans l’actualisation des données  
 Lors de l'importation de données dans un classeur PowerPivot, les connexions aux données externes sont souvent basées sur des connexions approuvées ou des connexions avec emprunt d'identité qui utilisent l'identité de l'utilisateur actuel pour se connecter à la source de données. Ces types de connexions fonctionnent uniquement lorsque l'utilisateur actuel a l'autorisation de lire les données importées.  
  
 Dans un scénario d'actualisation de données, la chaîne de connexion utilisée pour importer des données est réutilisée pour actualiser les données. Si la chaîne de connexion suppose qu'il s'agit de l'utilisateur actuel (par exemple, une chaîne qui inclut Integrated_Security=SSPI), le service système PowerPivot passera alors l'identité de l'utilisateur spécifié dans l'application cible en tant qu'utilisateur actuel. Cette connexion réussira uniquement si le compte a des autorisations en lecture sur la source de données externe.  
  
 C'est pourquoi vous devez accorder des autorisations de lecture seule au compte sur toutes les sources de données externes utilisées pendant l'actualisation des données.  
  
 Si vous êtes administrateur des sources de données utilisés dans votre organisation, vous pouvez créer une connexion et affecter les autorisations nécessaires. Dans le cas contraire, vous devez contacter les propriétaires des données et fournir les informations sur le compte. Veillez à spécifier le compte d'utilisateur de domaine Windows mappé à l'application cible. Il s’agit du compte que vous avez spécifié dans « étape 1 : créer une application cible » dans cette rubrique.  
  
###  <a name="bkmk_verify"></a>Étape 4 : vérifier la disponibilité du compte dans les pages de configuration de l’actualisation des données  
  
1.  Ouvrez une page de configuration de l'actualisation des données pour un classeur publié qui contient des données PowerPivot. Pour obtenir des instructions sur l’ouverture de la page, consultez [planifier une actualisation des données &#40;PowerPivot pour SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).  
  
2.  Vérifiez que l’option **se connecter à l’aide des informations d’identification enregistrées dans service Banque d’informations sécurisé (SSS) pour se connecter à la source de données** est activée dans la page Configuration de l’actualisation des données, puis entrez le nom de l’application cible.  
  
3.  Activez la case à cocher **aussi actualiser dès que possible** , puis cliquez sur **OK**.  
  
4.  Dans la bibliothèque qui contient le classeur, sélectionnez le classeur, cliquez sur la flèche vers le bas qui s’affiche à droite, puis sélectionnez **gérer l’actualisation des données PowerPivot**. Vous devrez peut-être attendre plusieurs minutes si le travail d'actualisation des données retourne une grande quantité de données.  
  
 Si une erreur se produit, vous pouvez cliquer sur **configurer la planification** dans la page historique d’actualisation des données pour essayer d’autres informations d’identification. Vous devrez également peut-être inspecter les informations de connexion à la source de données dans le classeur d'origine pour afficher la chaîne de connexion utilisée pendant l'actualisation des données. La chaîne de connexion fournira des informations sur l'emplacement du serveur et la base de données que vous pouvez utiliser pour résoudre le problème.  
  
 Pour plus d’informations sur la résolution des problèmes, consultez [résolution des problèmes d’actualisation des données PowerPivot](https://go.microsoft.com/fwlink/p/?LinkID=223279) sur le wiki technet.  
  
##  <a name="config3rd"></a>Configurer un compte prédéfini pour l’accès à des sources de données externes ou tierces  
 Les serveurs de base de données utilisent souvent leur propre méthode d'authentification. Si vous disposez d'un classeur PowerPivot qui nécessite des informations d'identification de base de données pour accéder à une source de données externe au cours de l'actualisation des données, vous pouvez créer un ID d'application cible pour les informations d'identification, puis spécifier l'application cible dans la section Sources de données de la page d'actualisation des données planifiée.  
  
 Cette étape est nécessaire uniquement si vous souhaitez proposer aux utilisateurs une option de remplacement des informations d'identification de base de données qui sont déjà incorporées dans le classeur PowerPivot.  
  
 Cette étape fonctionne seulement si la chaîne de connexion inclut déjà un nom d'utilisateur et un mot de passe. Notez que le fait d'avoir des informations d'identification dans la chaîne de connexion est relativement rare ; votre capacité à utiliser cette option est donc quelque peu limitée. Dans la plupart des cas, vous aurez seulement un ID d'utilisateur et un mot de passe dans la chaîne de connexion si vous utilisez l'authentification de base de données pour vous connecter à la source de données. Pour plus d’informations sur la vérification de la chaîne de connexion pour savoir si elle comprend un ID d’utilisateur et un mot de passe, consultez la section « accorder des autorisations pour créer des planifications et accéder aux données externes » dans l' [actualisation des données PowerPivot avec SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md).  
  
1.  Dans administration centrale, dans gestion des applications, cliquez sur **gérer les applications de service**.  
  
2.  Cliquez sur **service Banque d’informations sécurisé**.  
  
3.  Dans gérer les applications cibles, cliquez sur **nouveau**.  
  
4.  Dans ID d'application cible, tapez une chaîne de texte. La chaîne doit être unique, mais également facile à mémoriser. Les utilisateurs tapent cette chaîne dans les pages de planification de l'actualisation des données à chaque fois qu'ils veulent utiliser les informations d'identification stockées dans cette application.  
  
5.  Dans Nom complet, entrez un nom descriptif. Ce nom est utilisé uniquement à des fins d'affichage. Il n'est pas utilisé pour spécifier l'application cible dans une planification d'actualisation des données.  
  
6.  Dans Adresse de messagerie du contact, tapez votre adresse de messagerie.  
  
7.  Dans type d’application cible, sélectionnez **groupe**.  
  
8.  Ignorez l'URL de la page de l'application cible. L'actualisation des données PowerPivot ne l'utilise pas.  
  
9. Cliquez sur **Suivant**.  
  
10. Dans la page **spécifier les champs d’informations d’identification pour votre application cible de banque d’informations sécurisée** , acceptez les valeurs par défaut uniquement si la source de données utilise l’authentification Windows. Sinon, choisissez les types de champ valides pour votre source de données, puis modifiez les noms de champ afin qu'ils correspondent au type.  
  
     Par exemple, vous pouvez spécifier Nom d'utilisateur SQL Server et Mot de passe de l'utilisateur SQL Server pour les noms de champs, puis choisir Nom d'utilisateur et Mot de passe pour les types de champs.  
  
11. Cliquez sur Suivant.  
  
12. Dans Administrateurs d'applications cibles, spécifiez les comptes d'utilisateurs de domaine Windows des utilisateurs SharePoint qui doivent bénéficier d'un accès administrateur aux paramètres d'application.  
  
13. Dans Membres, ajoutez les comptes de groupes et d'utilisateurs suivants :  
  
    1.  En tant que créateur de l'application, ajoutez votre compte d'utilisateur Windows à la liste Membres.  
  
    2.  Ajoutez l'identité du pool d'applications de chaque application de service PowerPivot qui utilisera l'application cible pour accéder à ses informations d'identification stockées. Pour afficher l’identité, accédez à **gérer les applications de service**, sélectionnez l’application de service PowerPivot en cliquant sur l’espace vide en regard du nom (cela sélectionne la ligne), puis cliquez sur **Propriétés**. Le compte de sécurité qui apparaît dans cette page est le compte que vous souhaitez ajouter comme membre de l'application cible.  
  
    3.  Ajoutez les comptes d'utilisateur et de groupe Windows qui seront inclus dans cette application cible dans la section de sources de données d'une page de planification d'actualisation des données.  
  
14. Cliquez sur **OK**.  
  
15. Sélectionnez l’application cible que vous venez de créer, cliquez sur la flèche orientée vers le bas et sélectionnez **définir les informations d’identification.**  
  
16. Entrez les informations d'identification qui seront utilisées pour se connecter à la source de données (par exemple, le nom d'utilisateur et le mot de passe d'un compte de connexion SQL Server).  
  
17. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Planifier une actualisation des données &#40;PowerPivot pour SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)   
 [Actualisation des données PowerPivot avec SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)  
  
  
