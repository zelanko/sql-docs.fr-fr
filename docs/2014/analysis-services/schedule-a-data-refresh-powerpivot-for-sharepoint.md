---
title: Planifier une actualisation des données (PowerPivot pour SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: 8571208f-6aae-4058-83c6-9f916f5e2f9b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 58764334a6ee1902a09941e9fc9bb9723e517cdf
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53363841"
---
# <a name="schedule-a-data-refresh-powerpivot-for-sharepoint"></a>Planifier une actualisation des données (PowerPivot pour SharePoint)
  Vous pouvez planifier l'actualisation des données pour obtenir des mises à jour automatiques des données PowerPivot figurant dans un classeur Excel que vous avez publié sur un site SharePoint.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010  
  
 **Dans cette rubrique :**  
  
 [Conditions préalables](#prereq)  
  
 [Vue d’ensemble de l’actualisation des données](#intro)  
  
 [Activer et planifier l’actualisation des données](#drenablesched)  
  
 [Vérifier l’actualisation des données](#drverify)  
  
> [!NOTE]  
>  L'actualisation des données PowerPivot est effectuée par les instances de serveur Analysis Services de la batterie de serveurs SharePoint. Elle n'a aucun rapport avec la fonctionnalité d'actualisation des données proposée par Excel Services. La fonctionnalité d'actualisation de la planification des données PowerPivot n'actualise pas les données non-PowerPivot.  
  
##  <a name="prereq"></a> Conditions préalables  
 Pour créer une planification d'actualisation des données, vous devez disposer au moins du niveau d'autorisation Collaboration sur le classeur.  
  
 Les sources de données externes utilisées pendant l'actualisation des données doivent être disponibles et les informations d'identification que vous spécifiez dans la planification doivent avoir l'autorisation d'accéder à ces sources de données. L'actualisation des données planifiée requiert que l'emplacement des sources de données soit accessible sur une connexion réseau (par exemple, sur un partage de fichiers réseau plutôt qu'un dossier local sur votre station de travail).  
  
 La source de données ne peut pas être un document Office ou une base de données Access. Office ne prend pas en charge l'utilisation des composants de connectivité des données Office dans un environnement serveur. Si votre classeur contient des données de ces sources, veillez à les supprimer de la liste des sources de données dans votre planification d'actualisation des données.  
  
 Le classeur doit être de version [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] . Si vous utilisez des classeurs créés dans la version précédente de PowerPivot pour Excel, l'actualisation des données de planification ne fonctionnera que lorsque vous aurez effectué la mise à niveau de la base de données vers la version la plus récente.  
  
 Le classeur doit être archivé au moment où l'opération d'actualisation se termine. Un verrou sur le classeur est placé sur le fichier à la fin de l'actualisation des données, lorsque le fichier est enregistré, plutôt que lors du démarrage de l'actualisation.  
  
> [!NOTE]  
>  Le serveur ne verrouille pas le classeur pendant l'opération d'actualisation des données. Toutefois, il verrouille le fichier à la fin de l'actualisation des données en vue d'archiver le fichier mis à jour. Si actuellement, le fichier est extrait par un autre utilisateur, les données actualisées seront exclues. Pareillement, si le fichier est archivé mais est très différent de la copie récupérée par le serveur au début de l'actualisation, les données actualisées sont ignorées.  
  
##  <a name="intro"></a> Vue d’ensemble de l’actualisation des données  
 Les données PowerPivot dans un classeur Excel peuvent provenir de plusieurs sources de données externes, notamment de bases de données externes ou de fichiers de données auxquels vous accédez par des serveurs distants ou des partages de fichiers réseau. Pour les classeurs PowerPivot qui contiennent des données importées à partir de sources de données connectées ou externes, vous pouvez configurer l'actualisation des données de façon à planifier une importation automatique des données mises à jour de ces sources d'origine.  
  
 L'accès à une source de données externe s'effectue au moyen d'une chaîne de connexion incorporée, d'une URL ou d'un chemin d'accès UNC spécifié lors de l'importation des données d'origine dans le classeur à l'aide de l'application cliente PowerPivot. Les informations de connexion d'origine stockées dans le classeur PowerPivot sont réutilisées pour les opérations d'actualisation des données suivantes. Bien que vous puissiez remplacer les informations d'identification utilisées pour se connecter aux sources de données, vous ne pouvez pas remplacer les chaînes de connexion à des fins d'actualisation des données ; seules les informations de connexion existantes sont utilisées.  
  
 Il existe une seule page de planification d'actualisation des données pour chaque classeur, et toutes les informations de planification sont spécifiées dans cette page. En règle générale, c'est la personne qui a créé le classeur qui définit la planification.  
  
 En tant que propriétaire de la planification, vous pouvez effectuer les tâches suivantes :  
  
-   Définissez la planification par défaut. Il s'agit de la planification utilisée lorsqu'aucune planification n'est définie au niveau de la source de données.  
  
-   Spécifier les informations d'identification utilisées pour exécuter l'actualisation des données  
  
-   Choisissez les sources de données à inclure dans l'opération d'actualisation des données.  
  
-   Éventuellement, spécifiez les planifications et les informations d'identification individuelles en ligne pour chaque source de données interrogée pendant l'actualisation des données. Chaque source de données peut être actualisée indépendamment. Si vous créez des planifications personnalisées pour chaque source de données, la planification par défaut est ignorée.  
  
 La création de planifications avec précision pour des sources de données individuelles permet d'adapter la planification de l'actualisation aux fluctuations des sources de données externes. Par exemple, si une source de données externe contient des données transactionnelles générées pendant la journée, vous pouvez créer une planification d'actualisation des données individuelle pour cette source de données de façon à obtenir ses informations mises à jour de nuit.  
  
##  <a name="drenablesched"></a> Activer et planifier l’actualisation des données  
 Utilisez les instructions suivantes pour planifier l'actualisation des données PowerPivot d'un classeur Excel publié dans une bibliothèque SharePoint.  
  
1.  Dans la bibliothèque qui contient le classeur, sélectionnez ce dernier, puis cliquez sur la flèche orientée vers le bas pour afficher une liste de commandes.  
  
2.  Cliquez sur **Gérer l'actualisation des données PowerPivot**. Si une planification d'actualisation des données est déjà définie, vous verrez à la place la page Historique d'actualisation des données. Vous pouvez cliquer sur **Configurer l'actualisation des données** pour ouvrir la page de définition de la planification.  
  
3.  Dans la page de définition de la planification, sélectionnez la case à cocher **Activer** .  
  
4.  Dans Détails de la planification, spécifiez le type de planification et ses détails. Cette étape crée la planification par défaut.  
  
    > [!IMPORTANT]  
    >  Veillez à activer la case à cocher **Aussi actualiser dès que possible** . Cela vous permet de vérifier que l'actualisation des données est opérationnelle pour ce classeur. Notez qu'une fois que vous avez enregistré la planification, le démarrage de l'actualisation des données peut prendre jusqu'à une minute.  
  
5.  Dans Heure de début (au plus tôt), choisissez l'une des options suivantes :  
  
    1.  **Après les heures d'ouverture** spécifie une période de traitement en dehors des heures d'ouverture, lorsque les serveurs de base de données sont le plus susceptibles de contenir les données actuelles générées pendant la journée de travail.  
  
    2.  **Heure de début (au plus tôt) spécifique** est l'indication exacte (heure et minutes) de l'heure du jour la plus tôt où vous souhaitez que la demande d'actualisation des données soit ajoutée à une file d'attente de traitement. Les minutes peuvent être spécifiées par intervalles de 15 minutes. Ce paramètre s'applique au jour actuel, ainsi qu'à des dates dans le futur. Par exemple, si vous spécifiez une valeur de 6 h 30 du matin et qu'il est actuellement 4 h 30 de l'après-midi, la demande d'actualisation sera ajoutée à la file d'attente du jour actuel, car 4 h 30 de l'après-midi est ultérieur à 6 h 30 du matin.  
  
     L'heure de début au plus tôt définit le moment où une requête est ajoutée à la file d'attente de traitement. Le traitement en lui-même intervient lorsque le serveur dispose des ressources adéquates pour commencer le traitement des données. L'heure réelle du traitement est enregistrée dans l'historique d'actualisation des données à la fin du traitement.  
  
6.  Cochez la case **Aussi actualiser dès que possible** pour exécuter l'actualisation des données dès que le serveur peut traiter l'opération. Pour une actualisation des données réussie, il faut vérifier que les sources de données sont disponibles et que les autorisations et la configuration du serveur sont définies correctement.  
  
7.  Dans Notifications par courrier électronique, entrez l'adresse de messagerie de la personne qui doit être notifiée en cas d'erreur de traitement.  
  
8.  Dans les informations d'identification, spécifiez un compte qui sera utilisé pour exécuter le travail d'actualisation des données. Le compte doit avoir des autorisations de collaboration sur le classeur afin qu'il puisse ouvrir le classeur pour actualiser ses données. Il doit s'agir d'un compte d'utilisateur de domaine Windows. Dans de nombreux cas, ce compte doit également avoir des autorisations de lecture sur les sources de données externes utilisées pendant l'actualisation des données. Plus précisément, si vous avez importé à l'origine les données à l'aide de l'option Utiliser l'authentification Windows, la chaîne de connexion est construite pour utiliser les informations d'identification Windows de l'utilisateur actuel. Si l'utilisateur actuel correspond au compte d'actualisation des données, ce compte doit avoir des autorisations de lecture sur la source de données externe pour que l'actualisation des données réussisse. Choisissez l'une des options suivantes :  
  
    1.  Choisissez **Utilisez le compte d'actualisation des données configuré par l'administrateur** pour traiter l'opération d'actualisation des données à l'aide du compte d'actualisation des données PowerPivot sans assistance.  
  
    2.  Choisissez **Connectez-vous à l'aide des informations d'identification d'utilisateur Windows suivantes** si vous souhaitez entrer un nom d'utilisateur et un mot de passe. Entrez les informations de compte au format domaine\utilisateur.  
  
    3.  Choisissez **Connectez-vous à l'aide des informations d'identification enregistrées dans le Service Banque d'informations sécurisé** si vous connaissez l'ID d'une application cible qui contient les informations d'identification préalablement stockées que vous souhaitez utiliser.  
  
     Pour plus d’informations sur ces options, consultez [configurer les informations d’identification stockées pour l’actualisation des données PowerPivot &#40;PowerPivot pour SharePoint&#41; ](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md) et [configurer le compte d’actualisation des données PowerPivot sans assistance &#40;PowerPivot pour SharePoint&#41;](configure-unattended-data-refresh-account-powerpivot-sharepoint.md).  
  
9. Dans Sources de données, activez la case à cocher **Toutes les sources de données** si vous souhaitez que l'actualisation des données réinterroge l'ensemble des sources de données d'origine.  
  
     Si vous sélectionnez cette option, toute source de données externe qui fournit des données PowerPivot est automatiquement incluse dans l'actualisation, même si la liste des sources de données évolue à mesure que vous ajoutez ou supprimez des sources de données qui fournissent des données au classeur.  
  
     Désactivez la case à cocher **Toutes les sources de données** si vous souhaitez sélectionner manuellement les sources de données à inclure. Si, par la suite, vous modifiez le classeur en ajoutant une nouvelle source de données, veillez à mettre à jour la liste des sources de données dans la planification. Si vous ne le faites pas, les nouvelles sources de données ne seront pas incluses dans l'opération d'actualisation.  
  
     La liste des sources de données que vous pouvez sélectionner est récupérée du classeur PowerPivot lorsque vous ouvrez la page Gérer l'actualisation des données PowerPivot pour le classeur.  
  
     Veillez à ne sélectionner que des sources de données qui répondent aux critères suivants :  
  
    -   La source de données doit être disponible au moment où s'effectue l'actualisation des données et à l'emplacement indiqué. Si la source de données d'origine se trouve sur un lecteur de disque local de la personne qui a créé le classeur, vous devez soit exclure cette source de données de l'opération d'actualisation, soit trouver un moyen de publier cette source de données à un emplacement accessible via une connexion réseau. Si vous déplacez une source de données vers un emplacement réseau, veillez à ouvrir le classeur dans [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] et mettez à jour les informations de connexion à la source de données. Ces opérations sont nécessaires pour rétablir les informations de connexion stockées dans le classeur PowerPivot.  
  
    -   L'accès à la source de données doit se faire au moyen des informations d'identification incorporées dans le classeur PowerPivot ou de celles qui sont spécifiées dans la planification. Les informations d'identification incorporées sont stockées dans le classeur PowerPivot lorsque vous importez des données à l'aide de PowerPivot pour Excel. Les informations d'identification incorporées sont souvent sécurisées SSPI=IntegratedSecurity ou SSPI=TrustedConnection, ce qui signifie qu'elles utilisent les informations d'identification de l'utilisateur actuel pour se connecter à la source de données. Si vous souhaitez remplacer les informations d'identification dans votre planification d'actualisation des données, vous pouvez spécifier des informations d'identification prédéfinies et stockées. Pour plus d’informations, consultez [configurer les informations d’identification stockées pour l’actualisation des données PowerPivot &#40;PowerPivot pour SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
    -   L'actualisation des données doit réussir pour toutes les sources de données que vous spécifiez. Si ce n'est pas le cas, les données actualisées sont ignorées, vous laissant avec la dernière version enregistrée du classeur. Excluez toutes les sources de données pour lesquelles vous avez un doute.  
  
    -   L'actualisation des données ne doit pas invalider d'autres données de votre classeur. Lorsque vous actualisez un sous-ensemble de vos données, il est essentiel que vous compreniez si le classeur est toujours valide une fois les données les plus récentes agrégées avec les données statiques qui ne s'inscrivent pas sur la même période. En tant qu'auteur du classeur, il vous appartient de connaître les dépendances de vos données et de faire en sorte que l'actualisation des données soit appropriée pour le classeur lui-même.  
  
10. Vous pouvez éventuellement définir des planifications individuelles pour des sources de données spécifiques. Cela peut être utile si vous disposez de sources de données d'origine qui sont elles-mêmes mises à jour selon une planification. Par exemple, si une source de données PowerPivot utilise les données d'un mini-Data Warehouse actualisé chaque lundi à 02:00, vous pouvez définir une planification incluse pour le mini-Data Warehouse de façon à récupérer ses données actualisées chaque lundi à 04:00.  
  
11. Cliquez sur **OK** pour enregistrer la planification.  
  
##  <a name="drverify"></a> Vérifier l’actualisation des données  
 La meilleure méthode pour vérifier l'actualisation des données est de l'exécuter, puis de consulter la page d'historique pour voir se elle s'est terminée avec succès. En cochant la case **Aussi actualiser dès que possible** sur votre planification vous pouvez vérifier que l'actualisation des données fonctionne.  
  
 Vous pouvez consulter les opérations d'actualisation des données actuelles et passées dans la page Historique d'actualisation des données du classeur. Cette page ne s'affiche que si une actualisation des données a été planifiée pour un classeur. Si ce n'est pas le cas, c'est la page de définition de la planification qui s'affiche à la place.  
  
 Pour afficher l'historique d'actualisation des données, vous devez disposer d'autorisations Collaboration ou supérieures.  
  
1.  Sur un site SharePoint, ouvrez la bibliothèque qui contient un classeur PowerPivot.  
  
     Aucun indicateur visuel ne permet d'identifier les classeurs d'une bibliothèque SharePoint qui contiennent des données PowerPivot. Vous devez savoir à l'avance quels classeurs contiennent des données PowerPivot actualisables.  
  
2.  Sélectionnez le document, puis cliquez sur la flèche orientée vers le bas qui s'affiche à droite.  
  
3.  Sélectionnez **Gérer l'actualisation des données PowerPivot**.  
  
 La page d'historique s'affiche. Elle contient des informations complètes sur l'ensemble de l'activité d'actualisation des données PowerPivot du classeur Excel actif, notamment l'état de l'opération d'actualisation des données la plus récente.  
  
 Il peut arriver que vous constatiez des heures de traitement différentes de celles que vous avez spécifiées. Cela peut se produire si le serveur doit faire face à une charge de traitement importante. En cas de surcharge, l'instance du service [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] attend pour lancer l'actualisation des données que les ressources système soient à nouveau suffisantes.  
  
 Le classeur doit être archivé à l'heure où l'opération d'actualisation se termine. Le classeur est enregistré avec les données actualisées à la même heure. Si le fichier est extrait, l'actualisation des données est ignorée jusqu'à l'heure planifiée suivante.  
  
 Si un message d'état inattendu s'affiche (indiquant par exemple qu'une opération d'actualisation a échoué ou a été annulée), vous pouvez étudier le problème en vérifiant les autorisations et la disponibilité du serveur.  
  
 Examinez la page Résolution des problèmes d'actualisation des données PowerPivot sur le wiki TechNet pour obtenir de l'aide sur la résolution des problèmes d'actualisation des données. Pour plus d'informations, consultez [Résolution des problèmes d'actualisation des données PowerPivot](https://go.microsoft.com/fwlink/?LinkId=251594).  
  
> [!NOTE]  
>  Les administrateurs SharePoint peuvent vous aider à résoudre des problèmes d'actualisation des données en consultant les rapports d'actualisation des données consolidés dans le Tableau de bord de gestion PowerPivot dans l'Administration centrale. Pour plus d'informations, consultez [PowerPivot Management Dashboard and Usage Data](power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Actualisation des données PowerPivot avec SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md)   
 [Afficher l’historique d’actualisation des données &#40;PowerPivot pour SharePoint&#41;](power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)   
 [Configurer les informations d’identification stockées pour l’actualisation des données PowerPivot &#40;PowerPivot pour SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
  
