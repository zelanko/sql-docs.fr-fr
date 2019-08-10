---
title: Mettre à niveau PowerPivot pour SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 80ba9e43-f3f0-4730-9fb1-2afd2dd3e6fc
author: Minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d95ab3293a32bef22b2ffeeeef76ad0990892cf7
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68889067"
---
# <a name="upgrade-powerpivot-for-sharepoint"></a>Mettre à niveau PowerPivot pour SharePoint
  Cette rubrique résume les étapes nécessaires pour mettre à niveau un déploiement de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] vers [!INCLUDE[ssGeminiLong](../../includes/ssgeminilong-md.md)]. Les étapes spécifiques dépendent de la version de SharePoint exécutée par votre environnement et incluent le complément PowerPivot pour SharePoint (**spPowerPivot.msi**).  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010 | SharePoint 2013.  
  
 Pour obtenir les notes de mise à jour, consultez [Notes de mise à jour pour SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).  
  

  
## <a name="background"></a>Présentation  
  
-   Si vous mettez à niveau une batterie à plusieurs serveurs SharePoint 2010 qui a deux instances [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] ou plus, vous devez procéder à la mise à niveau complète de chaque serveur **avant** de passer au serveur suivant. Une mise à niveau complète implique l'exécution du programme d'installation de SQL Server pour mettre à niveau les fichiers programme [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] , puis d'effectuer les actions de mise à niveau de SharePoint qui permettent de configurer les services mis à niveau. La disponibilité du serveur est limitée jusqu'à l'exécution des actions de mise à niveau dans l'outil de configuration de PowerPivot approprié ou dans Windows PowerShell.  
  
-   Les instances du service système PowerPivot et du service Analysis Services d'une batterie de serveurs SharePoint 2010 doivent avoir la même version. Pour plus d'informations sur la vérification de la version, consultez la section [Vérifier les versions des composants et services PowerPivot](#bkmk_verify_versions) dans cette rubrique.  
  
-   Les outils de configuration PowerPivot constituent l'une des fonctionnalités partagées de SQL Server et toutes les fonctionnalités partagées sont mises à niveau en même temps. Si, au cours d'un processus de mise à niveau, vous sélectionnez d'autres fonctionnalités ou instances SQL Server qui nécessitent une mise à niveau de fonctionnalité partagée, l'outil de configuration de PowerPivot est également mis à niveau. Des problèmes peuvent survenir si l'outil de configuration PowerPivot est mis à niveau, alors que votre instance de PowerPivot ne l'est pas. Pour plus d’informations sur les fonctionnalités partagées de SQL Server, consultez [mise à niveau vers &#40;SQL Server&#41;2014 à l’aide de l’Assistant Installation](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md).  
  
-   Le complément PowerPivot pour SharePoint (**spPowerPivot.msi**) s'installe côte à côte avec les versions antérieures. Par exemple le complément [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] est installé dans le dossier `c:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools`.  
  

  
##  <a name="bkmk_prereq"></a> Conditions préalables  
 **autorisations**  
  
-   Vous devez être administrateur de la batterie de serveurs pour mettre à niveau une installation PowerPivot pour SharePoint. Vous devez être administrateur local pour exécuter le programme d'installation de SQL Server.  
  
-   Vous devez disposer des autorisations **db_owner** pour la base de données de configuration de la batterie.  
  
 **SQL Server :**  
  
-   Si l'installation existante PowerPivot est [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Service Pack 2 (SP2) est nécessaire pour une mise à niveau vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].  
  
-   Si l'installation existante PowerPivot est [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Service Pack 1 (SP1) est nécessaire pour une mise à niveau vers [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].  
  
 **SharePoint 2010 :**  
  
-   Si l'installation existante exécute SharePoint 2010, installez SharePoint 2010 Service Pack 2 avant la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Pour plus d'informations, consultez [Service Pack 2 pour Microsoft SharePoint 2010](https://www.microsoft.com/download/details.aspx?id=39672). Utilisez la commande PowerShell `(Get-SPfarm).BuildVersion.ToString()` pour vérifier la version. Pour référencer la version de la build à la date de version finale, consultez [Numéros de build SharePoint 2010](http://www.toddklindt.com/blog/Lists/Posts/Post.aspx?ID=224).  
  
 
  
##  <a name="bkmk_uprgade_sharepoint2013"></a> Mettre à niveau une batterie de serveurs SharePoint 2013 existante  
 Pour mettre à niveau [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] déployé dans SharePoint 2013, procédez comme suit :  
  
 ![PowerPivot pour la mise à niveau de SharePoint 2013](../../../2014/sql-server/install/media/as-powepivot-upgrade-flow-sharepoint2013.png "PowerPivot pour la mise à niveau de SharePoint 2013")  
  
1.  Exécutez le programme d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur un ou plusieurs serveurs principaux [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en mode SharePoint. Si le serveur héberge plusieurs instances d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], mettez au moins à niveau l'instance **POWERPIVOT** . Voici un récapitulatif des étapes de l'Assistant Installation relatives à la mise à niveau de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] :  
  
    1.  Dans l'Assistant Installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , cliquez sur **Installation**.  
  
    2.  Cliquez sur **Mettre à niveau à partir de SQL Server…** .  
  
    3.  Dans la page **Sélectionner une instance** , sélectionnez l'instance **POWERPIVOT** , puis cliquez sur **Suivant**.  
  
    4.  Pour plus d’informations, consultez [mettre à niveau vers SQL Server 2014 à &#40;l'&#41; aide de l’Assistant Installation](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
2.  Redémarrez le serveur.  
  
3.  Exécutez le complément [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint (**spPowerPivot.msi**) sur chaque serveur de la batterie SharePoint 2013 pour installer les fournisseurs de données. Les serveurs sur lesquels vous avez exécuté l'Assistant Installation de SQL Server, qui permet également la mise à niveau des fournisseurs de données, font exception. Pour plus d’informations, consultez [installer ou désinstaller le complément PowerPivot pour SharePoint &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013).  
  
4.  **Exécutez l'outil de configuration de PowerPivot pour SharePoint 2013** sur un des serveurs d'applications SharePoint pour configurer la batterie de serveurs SharePoint avec les fichiers de solution mis à jour installés par le complément. Vous ne pouvez pas utiliser l'Administration centrale SharePoint pour cette étape. Pour plus d’informations, consultez les rubriques suivantes :  
  
    1.  Dans la page de démarrage de Windows, tapez **PowerPivot** , puis dans les résultats de recherche, cliquez sur **Configuration de PowerPivot pour SharePoint 2013**. Notez que la recherche peut retourner les deux versions de l'outil de configuration.  
  
         ![Deux outils de configuration de PowerPivot](https://docs.microsoft.com/analysis-services/analysis-services/media/as-powerpivot-configtools-bothicons.gif "Deux outils de configuration de PowerPivot")  
  
         Ou  
  
         Dans le menu **Démarrer** , pointez sur **Tous les programmes**, puis sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], sur **Outils de configuration**, puis cliquez sur **Outil de configuration de PowerPivot pour SharePoint 2013**. Notez que cet outil est répertorié uniquement lorsque [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] est installé sur le serveur local.  
  
    2.  Au démarrage, l'outil de configuration vérifie l'état de mise à niveau des solutions de solution de la batterie de serveurs PowerPivot et de l'application Web PowerPivot. Si des versions antérieures de ces solutions sont détectées, vous verrez le**message «des versions plus récentes des fichiers de solution PowerPivot ont été détectées. Sélectionnez l’option de mise à niveau appropriée pour mettre à niveau votre batterie de serveurs** ». Cliquez sur **OK** pour fermer le message de validation système.  
  
    3.  Cliquez sur **Mettre à niveau des fonctionnalités, des services, des applications et des solutions**, puis cliquez sur **OK**.  
  
    4.  Passez en revue les actions dans la liste des tâches du volet gauche et excluez celles que l'outil ne doit pas réaliser. Toutes les actions sont incluses par défaut. Pour supprimer une action, sélectionnez-la dans la liste des tâches à gauche, puis désactivez la case à cocher **Inclure cette action dans la liste des tâches** sur la page **Paramètres** .  
  
    5.  Consultez éventuellement les informations détaillées figurant sous l'onglet **Script** ou l'onglet **Sortie** .  
  
         L'onglet Sortie est un résumé des actions qui seront effectuées par l'outil. Ces informations sont enregistrées dans les fichiers journaux à l’emplacement `C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\SPAddinConfiguration\Log`.  
  
         L'onglet Script affiche les applets de commande PowerShell ou référence les fichiers de script PowerShell qui seront exécutés par l'outil.  
  
    6.  Cliquez sur **Valider** pour vérifier si chaque action est valide. Si **Valider** n'est pas disponible, cela signifie que toutes les actions sont valides pour votre système. Si **Valider** est disponible, vous pouvez avoir modifié une valeur d’entrée (par exemple, le nom d’application de service Excel), ou l’outil peut avoir déterminé qu’une action particulière ne peut pas être exécutée. Si une action ne peut pas être effectuée, vous devez l'exclure ou résoudre les conditions sous-jacentes qui entraînent le marquage de l'action comme non valide.  
  
        > [!IMPORTANT]  
        >  La première action, **Mettre à niveau une solution de batterie de serveurs**, doit toujours être traitée en premier. Elle inscrit les applets de commande PowerShell qui sont utilisées pour configurer le serveur. Si vous obtenez une erreur sur cette action, ne continuez pas. À la place, utilisez les informations fournies par l'erreur pour diagnostiquer et résoudre le problème avant de traiter des actions supplémentaires dans la liste des tâches.  
  
    7.  Cliquez sur **Exécuter** pour exécuter toutes les actions qui sont valides pour cette tâche. **Exécuter** est disponible uniquement lorsque le contrôle de validation a réussi. Quand vous cliquez sur **Exécuter**, l’avertissement suivant s’affiche, vous rappelant que les actions sont traitées en mode batch : « **Tous les paramètres de configuration marqués comme étant valides dans l’outil seront appliqués à la batterie de serveurs SharePoint. Voulez-vous continuer ?**  ».  
  
    8.  Cliquez sur **OK** pour continuer.  
  
    9. La mise à niveau des solutions et des fonctionnalités de la batterie de serveurs peut prendre plusieurs minutes. Pendant ce temps, les demandes de connexion pour les données PowerPivot échouent avec des erreurs similaires à «**Impossible d’actualiser les données**» ou «**une erreur s’est produite lors de l’exécution de l’action demandée. Réessayez**. » Une fois la mise à niveau terminée, le serveur devient disponible et ces erreurs ne se produiront plus.  
  
     Pour plus d’informations, consultez les rubriques suivantes :  
  
    -   [Outils de configuration de PowerPivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools)  
  
    -   [Configurer ou réparer PowerPivot pour SharePoint outil &#40;de configuration de PowerPivot 2013&#41;](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-or-repair-power-pivot-for-sharepoint-2013)  
  
    -   [Configuration de PowerPivot à l’aide de Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell)  
  
    -   [Informations de référence sur PowerShell pour PowerPivot pour SharePoint](/sql/analysis-services/powershell/powershell-reference-for-power-pivot-for-sharepoint)  
  
5.  Vérifiez que la mise à niveau a réussi en effectuant les étapes postérieures à la mise à niveau et en vérifiant la version des serveurs PowerPivot de la batterie. Pour plus d'informations, consultez [Post-upgrade verification tasks](#verify) dans cette rubrique et la section suivante :  
  
 
  
##  <a name="bkmk_uprgade_sharepoint2010"></a> Mettre à niveau une batterie de serveurs SharePoint 2010 existante  
 Pour mettre à niveau [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] déployé dans SharePoint 2010, procédez comme suit :  
  
 ![Mise à niveau de PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/media/as-powepivot-upgrade-flow-sharepoint2010.png "Mise à niveau de PowerPivot pour SharePoint 2010")  
  
1.  Téléchargez le [Service Pack 2 pour Microsoft SharePoint 2010](https://www.microsoft.com/download/details.aspx?id=39672) et appliquez-le sur tous les serveurs de la batterie. Vérifiez que l'installation de SharePoint SP2 a réussi. Dans Administration centrale, dans la page Mise à niveau et migration, ouvrez la page Vérifier l'état d’installation du correctif et du produit pour afficher les messages d'état liés au SP2.  
  
2.  Vérifiez que le service Windows Administration SharePoint 2010 est en cours d'exécution.  
  
    ```  
    Get-Service | where {$_.displayname -like "*SharePoint*"}  
    ```  
  
3.  Vérifiez que les services **SQL Server Analysis Services** et **Service système SQL Server PowerPivot** de **SharePoint** sont démarrés dans l'Administration centrale de SharePoint ou utilisez la commande PowerShell suivante :  
  
    ```  
    get-SPserviceinstance | where {$_.typename -like "*sql*"}  
    ```  
  
4.  Vérifiez que le service **SQL Server Analysis Services (PowerPivot)** **Windows** est en cours d'exécution.  
  
    ```  
    Get-Service | where {$_.displayname -like "*powerpivot*"}  
    ```  
  
5.  **Exécutez[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] le programme d’installation** sur le premier serveur d’applications SharePoint qui exécute le service Windows **SQL Server Analysis Services (PowerPivot)** pour mettre à niveau l’instance PowerPivot. Dans la page Installation de l'Assistant Installation de SQL Server, choisissez l'option de mise à niveau. Pour plus d’informations, consultez [la &#40;page&#41;mise à niveau vers SQL Server 2014 à l’aide de l’Assistant Installation](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md).  
  
6.  **Redémarrez le serveur** avant d'exécuter l'outil de configuration. Cette étape vérifie que tous les éléments requis ou mises à jour installés par le programme d'installation de SQL Server sont entièrement configurés sur le système.  
  
7.  **Exécutez l’outil de configuration PowerPivot** sur le premier serveur d’applications SharePoint qui exécute le service SQL Server Analysis Services (PowerPivot) pour mettre à niveau les solutions et les services Web dans SharePoint. Vous ne pouvez pas utiliser l'Administration centrale pour cette étape.  
  
    1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, cliquez sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Outil de configuration PowerPivot**. Notez que cet outil est répertorié uniquement lorsque [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] est installé sur le serveur local.  
  
    2.  Au démarrage, l'outil de configuration vérifie l'état de mise à niveau des solutions de solution de la batterie de serveurs PowerPivot et de l'application Web PowerPivot. Si des versions antérieures de ces solutions sont détectées, vous verrez le message «des versions plus récentes des fichiers de solution PowerPivot ont été détectées. Sélectionnez l’option de mise à niveau appropriée pour mettre à niveau votre batterie de serveurs ». Cliquez sur **OK** pour fermer le message.  
  
    3.  Cliquez sur **Mettre à niveau des fonctionnalités, des services, des applications et des solutions**, puis sur **OK** pour continuer.  
  
    4.  L'avertissement suivant s’affiche : «Les classeurs du tableau de bord de gestion PowerPivot sont sur le point d’être mis à niveau vers la dernière version. Les personnalisations apportées aux classeurs existants seront perdues. Voulez-vous continuer ? ».  
  
         Cet avertissement fait référence aux classeurs du tableau de bord de gestion PowerPivot qui rendent compte de l'activité d'actualisation des données. Si vous avez personnalisé ces classeurs, toutes les modifications que vous avez apportées à ces classeurs seront perdues lorsque des fichiers existants seront remplacés par des versions plus récentes.  
  
         Cliquez sur **Oui** pour remplacer les classeurs par les versions plus récentes. Sinon, cliquez sur **Non** pour revenir à la page d'accueil. Enregistrez les classeurs à un emplacement différent de sorte de disposer d'une copie, puis revenez à cette étape lorsque vous êtes prêt à continuer.  
  
         Pour plus d'informations sur la personnalisation des classeurs utilisés dans le tableau de bord, consultez [Personnalisation du tableau de bord de gestion PowerPivot](https://go.microsoft.com/fwlink/?linkID=229639).  
  
    5.  Passez en revue les actions dans la liste des tâches et excluez celles que l'outil ne doit pas réaliser. Toutes les actions sont incluses par défaut. Pour supprimer une action, sélectionnez-la dans la liste des tâches, puis désactivez la case à cocher **Incluez cette action dans la liste des tâches** sur la page Paramètres.  
  
    6.  Consultez éventuellement les informations détaillées figurant sous l'onglet **Sortie** ou l'onglet **Script** .  
  
         L'onglet Sortie est un résumé des actions qui seront effectuées par l'outil. Ces informations sont enregistrées dans les fichiers journaux à l’emplacement `c:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\ConfigurationTool\Log`.  
  
         L'onglet Script affiche les applets de commande PowerShell ou référence les fichiers de script PowerShell qui seront exécutés par l'outil.  
  
    7.  Cliquez sur **Valider** pour vérifier si chaque action est valide. Si **Valider** n'est pas disponible, cela signifie que toutes les actions sont valides pour votre système. Si **Valider** est disponible, vous pouvez avoir modifié une valeur d’entrée (par exemple, le nom d’application de service Excel), ou l’outil peut avoir déterminé qu’une action particulière ne peut pas être exécutée. Si une action ne peut pas être effectuée, vous devez l'exclure ou résoudre les conditions sous-jacentes qui entraînent le marquage de l'action comme non valide.  
  
        > [!IMPORTANT]  
        >  La première action, **Mettre à niveau une solution de batterie de serveurs**, doit toujours être traitée en premier. Elle inscrit les applets de commande PowerShell qui sont utilisées pour configurer le serveur. Si vous obtenez une erreur sur cette action, ne continuez pas. À la place, utilisez les informations fournies par l'erreur pour diagnostiquer et résoudre le problème avant de traiter des actions supplémentaires dans la liste des tâches.  
  
    8.  Cliquez sur **Exécuter** pour exécuter toutes les actions qui sont valides pour cette tâche. **Exécuter** est disponible uniquement lorsque le contrôle de validation a réussi. Quand vous cliquez sur **Exécuter**, l’avertissement suivant s’affiche, vous rappelant que les actions sont traitées en mode batch : « Tous les paramètres de configuration marqués comme étant valides dans l’outil seront appliqués à la batterie de serveurs SharePoint. Voulez-vous continuer ? ».  
  
    9. Cliquez sur **OK** pour continuer.  
  
    10. La mise à niveau des solutions et des fonctionnalités de la batterie de serveurs peut prendre plusieurs minutes. Pendant ce temps, les demandes de connexion pour les données PowerPivot échouent avec des erreurs telles que «impossible d’actualiser les données» ou «une erreur s’est produite lors de l’exécution de l’action demandée. Réessayez. » Une fois la mise à niveau terminée, le serveur devient disponible et ces erreurs ne se produiront plus.  
  
8.  **Répétez le processus** pour chaque service d’SQL Server Analysis Services (PowerPivot) dans la batterie de serveurs: 1) exécutez le programme d’installation de SQL Server 2). Exécutez l’outil de configuration de PowerPivot.  
  
9. Vérifiez que la mise à niveau a réussi en effectuant les étapes postérieures à la mise à niveau et en vérifiant la version des serveurs PowerPivot de la batterie. Pour plus d'informations, consultez [Post-upgrade verification tasks](#verify) dans cette rubrique et la section suivante :  
  
10. **Dépannage des erreurs**  
  
     Vous pouvez afficher les informations d'erreur dans le volet Paramètres pour chaque action.  
  
     Pour les problèmes liés au déploiement ou la rétraction de solution, vérifiez que le service Administrateur SharePoint 2010 a démarré. Ce service exécute les travaux du minuteur qui déclenchent des modifications de configuration dans une batterie de serveurs. Si le service ne s'exécute pas, le déploiement ou la rétraction de solution échoue. Des erreurs persistantes indiquent qu'un travail existant de déploiement ou de rétraction figure déjà dans la file d'attente et bloque toute action supplémentaire depuis l'outil de configuration.  
  
    1.  Démarrez SharePoint 2010 Management Shell en tant qu'administrateur, puis exécutez la commande suivante pour afficher les travaux dans la file d'attente :  
  
        ```  
        Stsadm -o enumdeployments  
        ```  
  
    2.  Passez en revue les déploiements existants pour obtenir les informations suivantes : **Type** indique une rétraction ou un déploiement, **Fichier** correspond à powerpivotwebapp.wsp ou powerpivotfarm.wsp.  
  
    3.  Pour les déploiements ou les rétractions liés aux solutions PowerPivot, copiez la valeur GUID de **JobID** , puis collez-la dans la commande suivante (utilisez les commandes marquer, copier et coller dans le menu Edition de l’interpréteur de commandes pour copier le GUID):  
  
        ```  
        Stsadm -o canceldeployment -id "<GUID>"  
        ```  
  
    4.  Réexécutez la tâche dans l'outil de configuration en cliquant sur **Valider** suivi d' **Exécuter**.  
  
     Pour toutes les autres erreurs, vérifiez les journaux ULS. Pour plus d’informations, consultez [configurer et afficher les fichiers journaux SharePoint et &#40;la&#41;journalisation des diagnostics PowerPivot pour SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging).  
  

  
##  <a name="bkmk_workbooks"></a> Classeurs  
 La mise à niveau d'un serveur ne met pas nécessairement à niveau les classeurs PowerPivot qui s'y exécutent, mais les classeurs plus anciens créés dans la version précédente de PowerPivot pour Excel continuent de fonctionner comme avant, avec les fonctionnalités disponibles dans cette version. Les classeurs restent fonctionnels, car un serveur mis à niveau dispose de la version du fournisseur OLE DB Analysis Services qui faisait partie de l'installation antérieure.  
  
  
  
##  <a name="bkmk_datarefresh"></a> Actualisation des données  
 La mise à niveau a un impact sur les opérations d'actualisation des données. L'actualisation des données planifiée sur le serveur est disponible uniquement pour les classeurs qui correspondent à la version du serveur. Si vous hébergez des classeurs de la version antérieure, il est possible que l'actualisation des données ne fonctionne plus pour ces classeurs. Pour réactiver l'actualisation des données, vous devez mettre à niveau les classeurs. Vous pouvez mettre à niveau chaque classeur manuellement dans PowerPivot pour Excel ou activer la mise à niveau automatique pour la fonctionnalité d'actualisation des données dans SharePoint 2010. La mise à niveau automatique effectue la mise à niveau d'un classeur vers la version actuelle avant l'actualisation des données, ce qui permet aux opérations d'actualisation des données de respecter la planification établie.  
  

  
##  <a name="bkmk_verify_versions"></a>Vérifier les versions des composants et services PowerPivot  
 Toutes les instances du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] et d'Analysis Services doivent avoir la même version. Pour vérifier que tous les composants serveur utilisent la même version, contrôlez les informations de version des éléments suivants :  
  
### <a name="verify-the-version-of-powerpivot-solutions-and-the-powerpivot-system-service"></a>Vérifier la version de solutions PowerPivot et du service système PowerPivot  
 Exécutez la commande PowerShell suivante :  
  
```  
Get-PowerPivotSystemService  
```  
  
 Vérifiez **CurrentSolutionVersion**. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]est la version 12,0. \<> de build majeure. \<> de build mineure  
  
### <a name="verify-the-version-of-the-analysis-services-windows-service"></a>Vérifier la version du service Windows Analysis Services  
 Si vous n'avez mis à niveau que certains de vos serveurs [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] dans une batterie SharePoint 2010, l'instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur les serveurs qui n'ont pas été mis à niveau est plus ancienne que la version attendue dans la batterie. Vous devrez effectuer une mise à niveau de tous vos serveurs vers la même version pour permettre leur utilisation. Utilisez l’une des méthodes suivantes pour vérifier la version du service Windows SQL Server Analysis Services (PowerPivot) sur chaque ordinateur.  
  
 **Explorateur de fichiers Windows**:  
  
1.  Accédez au dossier **Bin** pour l'instance de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Par exemple, `C:\Program Files\Microsoft SQL Server\MSAS12.POWERPIVOT\OLAP\bin`.  
  
2.  Cliquez avec le bouton droit sur `msmdsrv.exe`, puis sélectionnez **Propriétés**.  
  
3.  Cliquez sur **Détails**.  
  
4.  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]la version du fichier doit être 12,00. \<> de build majeure. \<> de build mineure.  
  
5.  Vérifiez que ce numéro est identique à la version de solution PowerPivot et du service système.  
  
 **Informations sur le démarrage du service :**  
  
 Lorsque le service PowerPivot démarre, il écrit des informations de version dans le journal des événements Windows.  
  
1.  Exécuter Windows `eventvwr`  
  
2.  Créez un filtre pour la source `MSOLAP$POWERPIVOT`.  
  
3.  Rechercher un événement de niveau d'informations similaire au suivant  
  
     Service   démarré. Microsoft SQL Server Analysis Services 64 Bit Evaluation (x64) RTM **12.0.2000.8**.  
  
 **Utilisez PowerShell pour vérifier la version du fichier.**  
  
 Vous pouvez utiliser PowerShell pour vérifier la version du produit. PowerShell est un bon choix si vous souhaitez créer un script ou automatiser la vérification de la version.  
  
```  
(get-childitem "C:\Program Files\Microsoft SQL Server\MSAS12.POWERPIVOT2000\OLAP\bin\msmdsrv.exe").VersionInfo  
```  
  
 La commande PowerShell ci-dessus retourne des informations semblables aux suivantes :  
  
 ProductVersion   FileVersion           FileName  
  
 **12.0.2000.8** 2014.0120.200    C:\Program Files\Microsoft SQL Server\MSAS12.POWERPIVOT2000\OLAP\bin\msmdsrv.exe  
  
### <a name="verify-the-msolap-data-provider-version-on-sharepoint"></a>Vérifier la version du fournisseur de données MSOLAP sur SharePoint  
 Suivez les instructions suivantes pour vérifier quelles versions des fournisseurs OLE DB Analysis Services sont approuvées par Excel Services. Vous devez être l'administrateur de la batterie ou de l'application de service pour vérifier les paramètres du fournisseur de données approuvé d'Excel Services.  
  
1.  Dans l'Administration centrale, sous Gestion des applications, cliquez sur **Gérer les applications de service**.  
  
2.  Cliquez sur le nom de l'application de service Excel Services, par exemple **ExcelServiceApp1**.  
  
3.  Cliquez sur **Fournisseurs de données approuvés**. Vous devez voir MSOLAP.5 (Fournisseur Microsoft OLE DB pour OLAP Services 11.0). Si vous avez effectué la mise à niveau de votre installation [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] , vous verrez également MSOLAP.4 de la version antérieure.  
  
4.  Pour plus d'informations, consultez [Ajouter MSOLAP.5 en tant que fournisseur de données approuvé dans Excel Services](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/add-msolap-5-as-a-trusted-data-provider-in-excel-services).  
  
 MSOLAP.4 est décrit comme Fournisseur Microsoft OLE DB pour OLAP Services 10.0. Cette version peut être la version par défaut de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] installée avec Excel Services, ou ce peut être la version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] . La version par défaut que SharePoint installe ne prend pas en charge l'accès aux données PowerPivot. La version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] ou ultérieure doit se connecter aux classeurs PowerPivot sur SharePoint. Pour vérifier que vous disposez de la version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] , suivez les instructions de la section précédente qui expliquent comment vérifier la version en consultant les propriétés du fichier.  
  
### <a name="verify-the-adomdnet-data-provider-version"></a>Vérifier la version du fournisseur de données ADOMD.NET  
 Utilisez les instructions suivantes pour vérifier quelle version d'ADOMD.NET est installée. Vous devez être l'administrateur de la batterie ou de l'application de service pour vérifier les paramètres du fournisseur de données approuvé d'Excel Services.  
  
1.  Sur votre serveur d'applications SharePoint, accédez à `c:\Windows\Assembly`.  
  
2.  Triez par nom d'assembly et recherchez **Microsoft.Analysis Services.Adomd.Client**.  
  
3.  Vérifiez que vous disposez de la version 12,0. \<numéro de build >.  
  
  
  
##  <a name="geminifarm"></a>Mise à niveau de plusieurs serveurs PowerPivot pour SharePoint dans une batterie de serveurs SharePoint  
 Dans une topologie à plusieurs serveurs qui inclut plusieurs serveurs [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] , toutes les instances de serveur et tous les composants doivent avoir la même version. Le serveur qui exécute la version la plus récente du logiciel définit le niveau pour tous les serveurs de la batterie. Si vous ne mettez à niveau que quelques serveurs, ceux qui exécutent des versions antérieures du logiciel deviendront indisponibles jusqu'à ce qu'ils soient également mis à niveau.  
  
 Une fois le premier serveur à niveau, les serveurs supplémentaires qui n'ont pas encore été mis à niveau **deviennent indisponibles**. Leur disponibilité est restaurée une fois que tous les serveurs sont au même niveau.  
  
 L'installation de SQL Server met à niveau les fichiers de solution PowerPivot en place sur l'ordinateur physique, mais la mise à niveau des solutions utilisées par la batterie exige d'utiliser l'outil de configuration de PowerPivot décrit dans une section précédente de cette rubrique.  
  
 
  
##  <a name="qfe"></a>Application d’un correctif QFE à une instance PowerPivot dans la batterie de serveurs  
 L'application d'un correctif à un serveur PowerPivot pour SharePoint met à jour les fichiers programme existants vers une version plus récente qui inclut le correctif d'un problème spécifique. Lors de l'application d'un correctif QFE à une topologie à plusieurs serveurs, il n'y a aucun serveur principal par lequel commencer obligatoirement. Vous pouvez commencer par n'importe quel serveur tant que vous appliquez le même correctif QFE aux autres serveurs PowerPivot de la batterie.  
  
 Lorsque vous appliquez le correctif QFE, vous devez également effectuer une étape de configuration qui met à jour les informations de version du serveur dans la base de données de configuration de la batterie de serveurs. La version du serveur corrigé devient la nouvelle version attendue pour la batterie. Tant que le correctif QFE n'est pas appliqué et configuré sur tous les ordinateurs, les instances de PowerPivot pour SharePoint pour lesquelles le correctif QFE n'est pas disponible ne peuvent pas traiter les demandes de données PowerPivot.  
  
 Pour vous assurer que le correctif QFE est appliqué et configuré correctement, suivez les instructions suivantes :  
  
1.  Installez le correctif logiciel à l'aide des instructions fournies avec le correctif QFE.  
  
2.  Démarrez l'outil de configuration PowerPivot.  
  
3.  Cliquez sur **Mettre à niveau des fonctionnalités, des services, des applications et des solutions**, puis cliquez sur **OK**.  
  
4.  Passez en revue les actions incluses dans la tâche de mise à niveau, puis cliquez **Valider**.  
  
5.  Cliquez sur **Exécuter** pour appliquer les actions.  
  
6.  Répétez cette procédure pour des instances PowerPivot pour SharePoint supplémentaires dans la batterie de serveurs.  
  
    > [!IMPORTANT]  
    >  Dans un déploiement à plusieurs serveurs, assurez-vous de corriger et de configurer chaque instance avant de continuer à l'ordinateur suivant. L'outil de configuration de PowerPivot doit exécuter la tâche de mise à niveau pour l'instance actuelle avant de passer à l'instance suivante.  
  
 Pour vérifier les informations de version des services de la batterie de serveurs, utilisez la page **Vérifier l'état d’installation du correctif et du produit** dans la section Gestion des mises à niveau et des correctifs de l'Administration centrale.  
  
##  <a name="verify"></a> Tâches de vérification consécutives à la mise à niveau  
 Une fois la mise à niveau terminée, utilisez les étapes suivantes pour vérifier que le serveur est opérationnel.  
  
|Tâche|Lien|  
|----------|----------|  
|Vérifiez que le service fonctionne sur tous les ordinateurs qui exécutent PowerPivot pour SharePoint.|[Démarrer ou arrêter un service PowerPivot pour un serveur SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/start-or-stop-a-power-pivot-for-sharepoint-server)|  
|Vérifiez l'activation des fonctionnalités au niveau de la collection de sites.|[Activer l’intégration des fonctionnalités PowerPivot pour les collections de sites dans l’administration centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca)|  
|Vérifiez que les classeurs PowerPivot se chargent correctement en ouvrant un classeur et cliquant sur les filtres et les segments pour initialiser une requête.|Recherchez la présence de fichiers mis en cache sur le disque dur. La présence de fichiers mis en cache confirme que les fichiers de données ont été chargés sur ce serveur physique. Recherchez les fichiers mis en cache dans le dossier c:\Program Files\Microsoft SQL Server\MSAS12.POWERPIVOT\OLAP\Backup.|  
|Testez l'actualisation des données sur les classeurs sélectionnés configurés pour l'actualisation des données.|La méthode la plus simple pour tester l'actualisation des données consiste à modifier une planification d'actualisation des données, en activant la case à cocher **Aussi actualiser dès que possible** afin que l'actualisation des données s'exécute immédiatement. Cette étape détermine si l'actualisation des données aboutit pour le classeur actuel. Répétez ces étapes pour les autres classeurs fréquemment utilisés pour vous assurer que l'actualisation des données est fonctionnelle. Pour plus d’informations sur la planification de l’actualisation des données, consultez [planifier une actualisation &#40;des données PowerPivot pour SharePoint&#41;](../../../2014/analysis-services/schedule-a-data-refresh-powerpivot-for-sharepoint.md).|  
|Au fil du temps, vérifiez les rapports d'actualisation des données dans le tableau de bord de gestion PowerPivot pour vous assurer qu'il n'y a pas d'erreurs d'actualisation des données.|[Tableau de bord de gestion PowerPivot et données d’utilisation](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data)|  
  
 Pour plus d’informations sur la configuration des paramètres et des fonctionnalités PowerPivot, consultez [administration et configuration du serveur PowerPivot dans l’administration centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration).  
  
 Pour obtenir des instructions pas à pas qui vous guident dans toutes les tâches de configuration consécutives à l’installation, consultez [ &#40;configuration initiale PowerPivot pour SharePoint&#41;](../../../2014/sql-server/install/initial-configuration-powerpivot-for-sharepoint.md).  
  

  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Installation de PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
