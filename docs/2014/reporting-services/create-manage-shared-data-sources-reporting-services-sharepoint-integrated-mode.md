---
title: Créer et gérer des Sources de données partagées (Reporting Services en Mode intégré SharePoint) | Documents Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SharePoint integration [Reporting Services], shared data sources
- shared data sources [Reporting Services]
ms.assetid: 2d3428e4-a810-4e66-a287-ff18e57fad76
caps.latest.revision: 12
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: cab3d9ce31bff00af668a5a10567919bdd106b36
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139757"
---
# <a name="create-and-manage-shared-data-sources-reporting-services-in-sharepoint-integrated-mode"></a>Créer et gérer des sources de données partagées (Reporting Services en mode intégré SharePoint)
  Lorsque vous exécutez un rapport à partir d'une bibliothèque SharePoint, les informations de connexion peuvent être définies dans le rapport ou dans un fichier externe lié au rapport. Si les informations de connexion sont incorporées dans le rapport, elles constituent une source de données personnalisée. Si les informations de connexion sont définies dans un fichier externe, elles constituent une source de données partagée. Le fichier externe peut être un fichier de source de données du serveur de rapports (.rsds) ou un fichier de connexion de données Office (.odc).  
  
 Un fichier .rsds est similaire à un fichier .rds, mais possède un schéma différent. Pour créer un fichier .rsds, vous pouvez publier un fichier .rds issu du Concepteur de rapports ou du Générateur de modèles dans une bibliothèque SharePoint (un nouveau fichier .rsds est créé à partir du fichier .rds d'origine). Vous pouvez également créer un fichier dans une bibliothèque d'un site SharePoint.  
  
 Une fois que vous avez créé ou publié une source de données partagée, vous pouvez modifier les propriétés de connexion ou supprimer le fichier s'il n'est plus utilisé. Avant de supprimer une source de données partagée, vous devez déterminer si elle est utilisée par des rapports et des modèles de rapport. Pour cela, vous pouvez examiner les éléments dépendants qui font référence à la source de données partagée.  
  
 Bien que la liste des éléments dépendants indique si la source de données partagée est référencée, elle n'indique pas si l'élément est utilisé de manière active. Pour déterminer si la source de données partagée ou le modèle est utilisé de manière active, vous pouvez examiner les fichiers journaux du serveur de rapports. Si vous n'avez pas accès aux fichiers journaux ou si les fichiers ne contiennent pas les informations souhaitées, songez à déplacer le rapport vers un dossier inaccessible le temps de déterminer son état réel.  
  
### <a name="to-create-a-shared-data-source-rsds-file-sharepoint-2010"></a>Pour créer un fichier de source de données partagée (.rsds) (SharePoint 2010)  
  
1.  Cliquez sur l'onglet **Documents** dans le ruban de la bibliothèque.  
  
2.  Dans le menu **Nouveau document** , cliquez sur **Source de données du rapport**.  
  
    > [!NOTE]  
    >  Si l'élément **Source de données du rapport** ne figure pas dans le menu, cela signifie que le type de contenu de la source de données du rapport n'a pas été activé. Pour plus d’informations, consultez [ajouter Types serveur de rapports contenus dans une bibliothèque &#40;Reporting Services en Mode intégré SharePoint&#41;](../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).  
  
3.  Dans **Nom**, entrez un nom descriptif pour le fichier .rsds.  
  
4.  Dans **Type de source de données**, sélectionnez le type de source de données dans la liste. Pour plus d’informations, consultez [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
5.  Dans **Chaîne de connexion**, spécifiez un pointeur vers la source de données, ainsi que les autres paramètres nécessaires à l'établissement d'une connexion à la source de données externe. Le type de source de données utilisé détermine la syntaxe de la chaîne de connexion. Pour plus d’informations et d’exemples, consultez [des connexions de données, les Sources de données et les chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).  
  
6.  Dans **Informations d'identification**, spécifiez comment le serveur de rapports obtient les informations d'identification permettant d'accéder à la source de données externe. Les informations d'identification peuvent être stockées, demandées, intégrées ou configurées pour le traitement autonome des rapports.  
  
    -   Sélectionnez **Authentification Windows (intégrée)** pour pouvoir accéder aux données à l’aide des informations d’identification de l’utilisateur qui a ouvert le rapport. Ne sélectionnez pas cette option si la batterie de serveurs ou le site SharePoint utilise l'authentification par formulaire ou si la connexion au serveur de rapports s'effectue via un compte approuvé. Ne sélectionnez pas cette option si vous voulez planifier un abonnement ou un traitement de données pour ce rapport. Cette option convient mieux lorsque l'authentification Kerberos est activée pour votre domaine ou que la source de données se trouve sur le même ordinateur que le serveur de rapports. Si l'authentification Kerberos n'est pas activée, les informations d'identification Windows ne peuvent être transmises qu'à un seul autre ordinateur. En d'autres termes, si la source de données externe se trouve sur un autre ordinateur et si elle nécessite une connexion supplémentaire, vous recevrez une erreur au lieu des données attendues.  
  
    -   Sélectionnez **Demander des informations d'identification** pour que l'utilisateur entre ses informations d'identification chaque fois qu'il exécute le rapport. Ne sélectionnez pas cette option si vous voulez planifier un abonnement ou un traitement de données pour ce rapport.  
  
    -   Sélectionnez **Informations d'identification stockées** , si vous souhaitez accéder aux données via un jeu unique d'informations d'identification. Les informations d'identification sont chiffrées avant d'être stockées. Vous pouvez sélectionner les options appropriées pour déterminer le mode de stockage des informations d'identification. Sélectionnez l'option Utiliser les informations d'identification Windows si les informations d'identification stockées appartiennent à un compte d'utilisateur Windows. Sélectionnez l'option **Définir le contexte d'exécution pour ce compte** pour définir le contexte d'exécution sur le serveur de base de données. Pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bases de données, cette option définit la fonction SETUSER. Pour plus d’informations, consultez [SETUSER &#40;Transact-SQL&#41;](/sql/t-sql/statements/setuser-transact-sql).  
  
    -   Sélectionnez **Informations d’identification non requises** , si vous voulez spécifier les informations d’identification dans la chaîne de connexion, ou si vous voulez exécuter le rapport à l’aide d’un compte doté de privilèges minimaux et configuré sur le serveur de rapports. Si ce compte n'est pas configuré sur le serveur de rapports, les utilisateurs sont invités à fournir des informations d'identification ; par ailleurs, les opérations planifiées définies pour le rapport ne s'exécutent pas.  
  
7.  Sélectionnez **Activer cette source de données** si vous souhaitez que la source de données soit active. Si la source de données est configurée mais qu'elle n'est pas active, les utilisateurs verront un message d'erreur lorsqu'ils essaieront d'utiliser un rapport basé sur la source de données.  
  
8.  Cliquez sur le bouton **Tester la connexion** pour valider la configuration de la source de données.  
  
    > [!NOTE]  
    >  Le bouton Tester la connexion n'est pas pris en charge pour le type de source de données XML.  
  
9. Cliquez sur **OK** pour créer la source de données partagée.  
  
### <a name="to-view-dependent-items"></a>Pour afficher les éléments dépendants  
  
1.  Ouvrez la bibliothèque qui contient le fichier .rsds.  
  
2.  Pointez sur la source de données partagée.  
  
3.  Cliquez pour afficher une flèche orientée vers le bas, puis sélectionnez **Afficher les éléments dépendants**.  
  
     Pour les modèles de rapports, la liste des éléments dépendants affiche les rapports créés dans le Générateur de rapports. Pour les sources de données partagées, la liste des éléments dépendants peut inclure à la fois les rapports et les modèles de rapports.  
  
### <a name="to-delete-a-shared-data-source-rsds-file"></a>Pour supprimer un fichier de source de données partagée (.rsds)  
  
1.  Ouvrez la bibliothèque qui contient le fichier .rsds.  
  
2.  Pointez sur la source de données partagée.  
  
3.  Cliquez pour afficher une flèche orientée vers le bas et cliquez sur **Supprimer**.  
  
 Si vous supprimez par erreur une source de données partagée à conserver, vous pouvez en créer une autre qui contient les mêmes informations de connexion. Après avoir recréé la source de données partagée, ouvrez chaque rapport et modèle ayant utilisé cette source de données, puis sélectionnez la source de données partagée. Le nom, les informations d'identification ou la syntaxe de la chaîne de connexion du nouvel élément de source de données partagée peuvent être différents de ceux que vous supprimez. Tant que la connexion correspond à la même source de données, les propriétés de la source de données peuvent différer des valeurs d'origine.  
  
 Soyez vigilant lorsque vous supprimez un modèle de rapport. Si vous supprimez un modèle, vous ne pouvez plus ouvrir et modifier les rapports qui en dépendent dans le Générateur de rapports. Si vous supprimez par inadvertance un modèle utilisé par des rapports existants, vous devez générer de nouveau le modèle, recréer et enregistrer tous les rapports qui utilisent ce modèle, puis spécifier de nouveau la sécurité des éléments de modèle à utiliser. Vous ne pouvez pas simplement générer de nouveau le modèle, puis l'associer à un rapport existant.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier des informations d'identification et de connexion pour les sources de données de rapports](report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  
