---
title: Configurer le compte d’actualisation des données PowerPivot sans assistance (PowerPivot pour SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 81401eac-c619-4fad-ad3e-599e7a6f8493
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 894e7d4fb5a0234643cf237e767a8ae999e67496
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087420"
---
# <a name="configure-the-powerpivot-unattended-data-refresh-account-powerpivot-for-sharepoint"></a>Configurer le compte d'actualisation des données PowerPivot sans assistance (PowerPivot pour SharePoint)
  Le compte d'actualisation des données PowerPivot sans assistance est un compte désigné pour l'exécution de travaux d'actualisation des données PowerPivot dans une batterie de serveurs SharePoint. En le configurant, vous activez l’option **utiliser le compte d’actualisation des données configuré par l’administrateur** dans une page planification de l’actualisation des données (voir ci-dessous). Les auteurs de classeurs qui planifient l'actualisation des données peuvent choisir cette option s'ils souhaitent utiliser le compte d'actualisation des données PowerPivot sans assistance pour exécuter un travail d'actualisation des données. Pour plus d’informations sur la façon d’afficher les options d’informations d’identification dans une planification d’actualisation des données, consultez [planifier une actualisation des données &#40;PowerPivot pour SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).  
  
 ![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010  
  
 En fonction des options que vous avez sélectionnées lors de la configuration du serveur, il est possible que le compte d'actualisation des données sans assistance soit déjà créé. Dans une configuration par défaut, l'identité du compte d'actualisation des données sans assistance est définie initialement sur le compte de batterie de serveurs. Vous pouvez améliorer la sécurité de votre déploiement en modifiant le compte pour l'exécuter en tant qu'un autre utilisateur. Suivez ces instructions pour modifier le compte : [mettre à jour les informations d’identification utilisées par un compte d’actualisation des données PowerPivot sans assistance existant](#bkmk_editUA).  
  
 Pour tous les autres scénarios d'installation, vous devez configurer ce compte manuellement à l'aide des instructions ci-dessous.  
  
 Cette rubrique contient les sections suivantes :  
  
 [Prérequis](#bkmk_prereq)  
  
 [Étape 1 : créer une application cible et définir les informations d'identification](#bkmk_create)  
  
 [Étape 2 : spécifier le compte sans assistance dans les pages de configuration de serveur PowerPivot](#bkmk_specifyUA)  
  
 [Étape 3 : accorder des autorisations collaboration au compte](#bkmk_grant)  
  
 [Étape 4 : accorder des autorisations de lecture pour accéder aux sources de données externes utilisées dans l'actualisation des données](#bkmk_dbread)  
  
 [Étape 5 : vérifier la disponibilité du compte dans les pages de configuration de l'actualisation des données](#bkmk_verify)  
  
 [Utilisation du compte d'actualisation des données PowerPivot sans assistance.](#bkmk_use)  
  
 [Mettre à jour les informations d'identification utilisées par un compte d'actualisation des données PowerPivot sans assistance existant](#bkmk_editUA)  
  
##  <a name="bkmk_prereq"></a>Conditions préalables  
 Le service Banque d'informations sécurisé doit être activé et configuré et une clé principale doit être générée. Pour obtenir des instructions sur la procédure à suivre, consultez [actualisation des données PowerPivot avec SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)  
  
 Vous devez décider à l'avance quel sera le compte d'utilisateur de domaine Windows à utiliser comme compte d'actualisation des données PowerPivot sans assistance. Il doit s'agir d'un compte spécifiquement créé dans ce but, afin que vous puissiez surveiller son utilisation.  
  
 Vous devez connaitre l'identité de l'application du service système PowerPivot. Vous accordez à ce compte de service des autorisations **contrôle total** sur le compte d’actualisation des données sans assistance lorsque vous créez l’application cible à l’étape 1. Ces autorisations permettent au service système PowerPivot de récupérer les informations d'identification du compte d'actualisation des données sans assistance pendant l'actualisation des données. Pour accéder aux informations de compte de service requises, ouvrez la page **configurer les comptes de service** dans l’administration centrale et sélectionnez le pool d’applications de service utilisé par l’application de service PowerPivot. Par défaut, il s’agit du **pool d’applications de service-système des services Web SharePoint**.  
  
## <a name="configure-the-unattended-powerpivot-data-refresh-account"></a>Configurer le compte d'actualisation des données PowerPivot sans assistance  
 Vous pouvez configurer un seul compte d'actualisation des données PowerPivot sans assistance pour chaque application de service PowerPivot. Les informations sur le compte sont stockées dans le service Banque d'informations sécurisé dans une application cible définie sur un compte d'utilisateur de domaine Windows prédéfini. Une fois l'application cible créée, vous pouvez la spécifier comme compte d'actualisation des données PowerPivot dans les pages de configuration d'une application de service PowerPivot.  
  
> [!NOTE]  
>  Lorsque l'actualisation des données est effectuée sous le compte d'actualisation des données sans assistance, l'historique de création de rapports d'utilisation et de l'actualisation des données est enregistré sur le compte d'utilisateur Windows utilisé pour l'actualisation des données sans assistance. Si vous avez besoin d'un enregistrement plus précis des individus qui demandent une actualisation des données ou qui possèdent des planifications, envisagez une autre option pour l'exécution de l'actualisation des données. À savoir, faire spécifier aux utilisateurs leurs propres informations d'identification (c'est la valeur par défaut), ou créer des applications cibles supplémentaires pour stocker les informations d'identification Windows que vous souhaitez utiliser à des fins d'actualisation des données. Pour plus d’informations, consultez [configurer les informations d’identification stockées pour l’actualisation des données PowerPivot &#40;PowerPivot pour SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
 La création du compte d'actualisation des données sans assistance comprend cinq parties.  
  
-   Créez une application cible dans le service Banque d'informations sécurisé pour le compte et spécifiez les informations d'identification.  
  
-   Spécifiez l'ID d'application cible pour le compte d'actualisation des données sans assistance dans la page de configuration du serveur PowerPivot.  
  
-   Accordez des autorisations Collaboration au compte.  
  
-   Accordez des autorisations de lecture sur le compte pour accéder aux sources de données externes pendant l'actualisation des données.  
  
-   Vérifiez que le compte est disponible dans la page de planification Gérer l'actualisation des données pour un classeur PowerPivot publié.  
  
###  <a name="bkmk_create"></a>Étape 1 : créer une application cible et définir les informations d’identification  
  
1.  Dans administration centrale, dans gestion des applications, cliquez sur **gérer les applications de service**.  
  
2.  Cliquez sur **service Banque d’informations sécurisé**.  
  
3.  Dans gérer les applications cibles, cliquez sur **nouveau**.  
  
4.  Dans ID de l’application cible, tapez **PowerPivotDataRefresh**.  
  
5.  Dans nom d’affichage, tapez **actualisation des données PowerPivot**.  
  
6.  Dans Adresse de messagerie du contact, tapez votre adresse de messagerie.  
  
7.  Dans type d’application cible, sélectionnez **individuel**.  
  
    > [!NOTE]  
    >  La spécification d'un type de compte individuel est correcte pour ce scénario, car seule l'application de service PowerPivot demandera les informations d'identification du compte d'actualisation des données PowerPivot sans assistance. En pratique, l'application de service est le seul utilisateur du compte d'actualisation des données sans assistance ; le type de compte individuel pour cette application cible représente donc le meilleur choix.  
  
8.  Ignorez l'URL de la page de l'application cible. L'actualisation des données PowerPivot ne l'utilise pas.  
  
9. Cliquez sur **Suivant**.  
  
10. Dans la page **spécifier les champs d’informations d’identification pour votre application cible de banque d’informations sécurisée** , acceptez les valeurs par défaut. Les noms et types de champ doivent être Nom d'utilisateur Windows et Mot de passe Windows.  
  
11. Cliquez sur **Suivant**.  
  
12. Dans les administrateurs d'applications cibles, spécifiez l'identité du pool d'applications de l'application de service PowerPivot. Le service requiert des autorisations **contrôle total** pour pouvoir récupérer les informations de compte d’actualisation des données sans assistance au moment de l’exécution. De plus, spécifiez les comptes d'utilisateurs de domaine Windows des utilisateurs SharePoint qui doivent bénéficier d'un accès administrateur aux paramètres d'application.  
  
13. Cliquez sur **OK**.  
  
14. Sélectionnez l’application cible que vous venez de créer, cliquez sur la flèche orientée vers le bas et sélectionnez **définir les informations d’identification.**  
  
15. Dans **propriétaires des informations d’identification**, tapez un compte d’utilisateur de domaine Windows pour lequel vous souhaitez disposer des autorisations nécessaires pour mettre à jour les informations d’identification. Les informations d’identification sont utilisées pour les actions d’actualisation des données et les **propriétaires des informations d’identification** sont autorisés à modifier les informations d’identification.  
  
16. Cliquez sur **OK**.  
  
###  <a name="bkmk_specifyUA"></a>Étape 2 : spécifier le compte sans assistance dans les pages de configuration du serveur PowerPivot  
  
1.  Dans administration centrale, dans gestion des applications, cliquez sur **gérer les applications de service**.  
  
2.  Recherchez l'application de service PowerPivot. Vous pouvez reconnaître une application de service à son type. Un type d'application de service PowerPivot est **Application de service PowerPivot**.  
  
3.  Cliquez sur le nom de l'application de service PowerPivot. Attendez que le tableau de bord de gestion PowerPivot s'affiche.  
  
4.  Dans actions, dans le coin supérieur droit, cliquez sur **configurer les paramètres d’application de service**.  
  
5.  Dans actualisation des données, dans le compte d’actualisation des données PowerPivot sans assistance, tapez l’ID d’application cible que vous avez créé à l’étape précédente : **PowerPivotDataRefresh**.  
  
6.  Cliquez sur **OK**.  
  
###  <a name="bkmk_grant"></a>Étape 3 : accorder des autorisations collaboration au compte  
 Avant de pouvoir utiliser le compte d'actualisation des données PowerPivot sans assistance, il faut attribuer des autorisations Collaboration sur tous les classeurs PowerPivot pour lequel il est utilisé. Ce niveau d'autorisation est nécessaire pour ouvrir le classeur d'une bibliothèque, puis l'enregistrer à nouveau dans la bibliothèque une fois les données actualisées.  
  
 L'affectation d'autorisations est une procédure effectuée par l'administrateur de collection de sites. Les autorisations SharePoint peuvent être affectées à la collection de sites racine ou à n'importe quel niveau inférieur, notamment aux documents individuels et aux éléments. La manière dont vous définissez les autorisations dépendra du degré de granularité que vous souhaitez. Les étapes suivantes vous montrent une méthode d'affectation des autorisations.  
  
1.  Sur un site SharePoint, dans actions du site, cliquez sur **autorisations du site**.  
  
2.  Cliquez sur **Accorder des autorisations**.  
  
3.  Dans Sélectionnez les utilisateurs, tapez le nom du compte d'utilisateur de domaine Windows que vous avez désigné comme compte PowerPivot sans assistance. Il s'agit du nom du compte d'utilisateur de domaine Windows que vous avez spécifié dans application cible dans le service Banque d'informations sécurisé.  
  
4.  Dans accorder des autorisations, sélectionnez **accorder directement les**autorisations des utilisateurs.  
  
5.  Sélectionnez **collaboration**, puis cliquez sur **OK**.  
  
###  <a name="bkmk_dbread"></a>Étape 4 : accorder des autorisations de lecture pour accéder aux sources de données externes utilisées dans l’actualisation des données  
 Lors de l'importation de données dans un classeur PowerPivot, les connexions aux données externes sont souvent basées sur des connexions approuvées ou des connexions avec emprunt d'identité qui utilisent l'identité de l'utilisateur actuel pour se connecter à la source de données. Ces types de connexions fonctionnent uniquement lorsque l'utilisateur actuel a l'autorisation de lire les données importées.  
  
 Dans un scénario d'actualisation de données, la chaîne de connexion utilisée pour importer des données est réutilisée pour actualiser les données. Si la chaîne de connexion suppose qu'il s'agit de l'utilisateur actuel (par exemple, une chaîne qui inclut Integrated_Security=SSPI), le service système PowerPivot passera alors l'identité de l'utilisateur du compte d'actualisation des données PowerPivot sans assistance en tant qu'utilisateur actuel. Cette connexion réussira uniquement si le compte d'actualisation des données PowerPivot sans assistance a des autorisations en lecture sur la source de données externe.  
  
 Pour cette raison, vous devez accorder des autorisations en lecture seule au compte d'actualisation des données PowerPivot sans assistance sur toutes les sources de données externes utilisées dans les opérations d'actualisation des données qui s'exécutent sous le compte sans assistance.  
  
 Si vous êtes administrateur des sources de données utilisés dans votre organisation, vous pouvez créer une connexion et affecter les autorisations nécessaires. Dans le cas contraire, vous devez contacter les propriétaires des données et fournir les informations sur le compte. Veillez à spécifier le compte d'utilisateur de domaine Windows mappé au compte d'actualisation des données PowerPivot sans assistance. Il s’agit du compte que vous avez spécifié dans « (étape 1) : créer une application cible et définir les informations d’identification » dans cette rubrique.  
  
###  <a name="bkmk_verify"></a>Étape 5 : vérifier la disponibilité du compte dans les pages de configuration de l’actualisation des données  
  
1.  Ouvrez une page de configuration de l'actualisation des données pour un classeur publié qui contient des données PowerPivot. Pour obtenir des instructions sur l’ouverture de la page, consultez [planifier une actualisation des données &#40;PowerPivot pour SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md).  
  
2.  Vérifiez que l’option **utiliser le compte d’actualisation des données configuré par l’administrateur** est activée dans la page Configuration de l’actualisation des données.  
  
3.  Activez la case à cocher **aussi actualiser dès que possible** , puis cliquez sur **OK**.  
  
4.  Dans la bibliothèque qui contient le classeur, sélectionnez le classeur, cliquez sur la flèche vers le bas qui s’affiche à droite, puis sélectionnez **gérer l’actualisation des données PowerPivot**. Vous devrez peut-être attendre plusieurs minutes si le travail d'actualisation des données retourne une grande quantité de données.  
  
 Si une erreur se produit, vous pouvez cliquer sur **configurer la planification** dans la page historique d’actualisation des données pour essayer d’autres informations d’identification. Vous devrez également peut-être inspecter les informations de connexion à la source de données dans le classeur d'origine pour afficher la chaîne de connexion utilisée pendant l'actualisation des données. La chaîne de connexion fournira des informations sur l'emplacement du serveur et la base de données que vous pouvez utiliser pour résoudre le problème.  
  
 Pour plus d’informations sur la résolution des problèmes, consultez [résolution des problèmes d’actualisation des données PowerPivot](https://go.microsoft.com/fwlink/p/?LinkID=223279) sur le wiki technet.  
  
##  <a name="bkmk_use"></a>Utilisation du compte d’actualisation des données PowerPivot sans assistance  
 Parmi les trois options d'informations d'identification dans la page de planification de l'actualisation des données PowerPivot, seule le première correspond au compte d'actualisation des données sans assistance. Veillez à sélectionner cette option lors de la configuration de la planification d'actualisation des données.  
  
 ![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")  
  
 N'utilisez pas la troisième option (celle qui requiert que vous entriez l'ID d'application cible) pour accéder au compte d'actualisation des données PowerPivot sans assistance. Un contrôle de l'emprunt d'identité supplémentaire est effectué avec cette option, qui provoquera une erreur de validation si vous essayez de l'utiliser avec le compte d'actualisation des données PowerPivot sans assistance (ou toute application cible basée sur le compte de type individuel). Pour plus d’informations sur l’utilisation de la troisième option, consultez [configurer les informations d’identification stockées pour l’actualisation des données PowerPivot &#40;PowerPivot pour SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
##  <a name="bkmk_editUA"></a>Mettre à jour les informations d’identification utilisées par un compte d’actualisation des données PowerPivot sans assistance existant  
 Si le compte d'actualisation des données sans assistance a déjà été configuré par l'installation ou par un administrateur, vous pouvez mettre à jour le nom d'utilisateur ou le mot de passe en modifiant l'application cible qui stocke les informations d'identification. Notez que l'identité Windows d'origine associée précédemment au compte d'actualisation des données PowerPivot sans assistance ne sera pas visible lorsque vous modifiez les informations d'identification dans le service Banque d'informations sécurisé. Si vous mettez à jour un mot de passe arrivé à expiration ou spécifiez un autre compte, vous devez toujours retaper à la fois le nom d'utilisateur et le mot de passe pour cette application cible dans le service Banque d'informations sécurisé.  
  
1.  Dans administration centrale, dans gestion des applications, cliquez sur **gérer les applications de service**.  
  
2.  Cliquez sur **service Banque d’informations sécurisé**.  
  
3.  Activez la case à cocher en regard de **PowerPivotDataRefresh**.  
  
4.  Dans informations d’identification, cliquez sur **définir**.  
  
5.  Dans **propriétaires des informations d’identification**, tapez un compte d’utilisateur de domaine Windows pour lequel vous souhaitez disposer des autorisations nécessaires pour mettre à jour les informations d’identification. Les informations d’identification sont utilisées pour les actions d’actualisation des données et les **propriétaires des informations d’identification** sont autorisés à modifier les informations d’identification.  
  
6.  Dans Nom d'utilisateur, tapez le compte d'utilisateur de domaine Windows qui fera partie des informations d'identification d'actualisation des données sans assistance.  
  
7.  Dans Mot de passe, entrez le mot de passe du compte, puis entrez-le à nouveau pour le confirmer.  
  
8.  Cliquez sur **OK**.  
  
 Si vous modifiez non seulement le mot de passe, mais également le nom d'utilisateur de compte, vous devrez très probablement effectuer des étapes de configuration supplémentaires, telles qu'accorder des autorisations de lecture pour accéder aux sources de données externes et des autorisations SharePoint pour mettre à jour le classeur PowerPivot. Pour obtenir des instructions, consultez la section Configuration du compte d’actualisation des données PowerPivot sans assistance : [étape 3 : accordez des autorisations de collaboration au compte](#bkmk_grant), puis poursuivez avec les étapes restantes, en concluant avec la vérification que le compte est correctement configuré.  
  
## <a name="see-also"></a>Voir aussi  
 [Actualisation des données PowerPivot avec SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)   
 [Planifier une actualisation des données &#40;PowerPivot pour SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)   
 [Actualisation des données PowerPivot](power-pivot-sharepoint/power-pivot-data-refresh.md)  
  
  
