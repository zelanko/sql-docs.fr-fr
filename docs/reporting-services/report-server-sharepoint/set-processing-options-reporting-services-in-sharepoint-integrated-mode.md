---
title: "Définir les Options de traitement (Reporting Services en Mode intégré SharePoint) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint integration [Reporting Services], content management
- snapshots [Reporting Services], creating
ms.assetid: 453b19a1-739a-4b67-aeea-2069b52204e1
caps.latest.revision: 15
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8f2a5c52f4fa9b04026490c1e66243bf0d660c13
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="set-processing-options-reporting-services-in-sharepoint-integrated-mode"></a>Définir les options de traitement (Reporting Services en mode intégré SharePoint)
  Vous pouvez définir des options de traitement sur un rapport [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour déterminer le moment où le traitement des données a lieu. Vous pouvez également définir une valeur d'expiration pour le traitement des rapports, ainsi que des options qui déterminent si l'historique du rapport en cours est activé.  
  
-   Vous pouvez exécuter un rapport en tant qu'instantané de rapport afin d'éviter qu'il soit exécuté à des moments inopportuns (par exemple, pendant une sauvegarde programmée). En général, un instantané de rapport est créé et actualisé ultérieurement selon une planification, vous permettant ainsi de déterminer précisément le moment auquel le traitement du rapport et des données se produit. Si un rapport est basé sur des requêtes dont l'exécution est longue ou qui utilisent des données d'une source de données que vous ne souhaitez pas rendre accessible à certaines heures, vous devez exécuter le rapport en tant qu'instantané.  
  
-   Un serveur de rapports peut mettre en mémoire cache la copie d'un rapport traité et retourner cette copie lorsqu'un utilisateur ouvre le rapport. La mise en cache est une technique d'optimisation des performances. La mise en cache peut raccourcir le temps nécessaire à la récupération d'un rapport si celui-ci est volumineux ou fréquemment consulté.  
  
-   L'historique de rapport est un ensemble de copies d'un rapport ayant fait l'objet d'une exécution précédente. Vous pouvez utiliser l'historique de rapport pour conserver un enregistrement d'un rapport dans le temps. L'historique de rapport ne convient pas aux rapports contenant des données confidentielles ou des données personnelles. Pour cette raison, l'historique de rapport peut inclure uniquement les rapports qui interrogent une source de données à l'aide d'un ensemble unique d'informations d'identification (soit stockées, soit utilisées pour l'exécution de rapport sans assistance) qui sont mises à la disposition de tous les utilisateurs qui exécutent un rapport.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] avec SharePoint utilise les fonctionnalités de gestion du contenu extrait et archivé de SharePoint pour enregistrer les mises à jour des types de contenu de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Cela inclut la création d'instantanés de rapports. Par conséquent, si vous avez activé le contrôle de version sur une bibliothèque de documents, vous verrez la version actualisée du rapport lorsqu'une nouvelle capture instantanée d'historique de rapport est créée. Il s'agit d'un effet secondaire de la mise à jour des captures d'instantanés. Lorsqu'un instantané est mis à jour, la propriété LastExecution du rapport est modifiée, ce qui modifie la version du rapport.  
  
-   Vous pouvez spécifier des valeurs de délai d'attente pour fixer des limites à l'utilisation des ressources système.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode|  
  
 **Dans cette rubrique :**  
  
-   [Pour définir les options d'actualisation des données](#bkmk_set_data_refresh)  
  
-   [Pour définir les options de mise en cache de rapport](#bkmk_set_report_caching)  
  
-   [Pour définir des délais d'expiration de traitement](#bkmk_set_processing)  
  
-   [Pour définir les options et limites de l'historique de rapport](#bkmk_set_report_history)  
  
-   [Définir le délai d'attente de base de données](#bkmk_set_database_timeout)  
  
##  <a name="bkmk_set_data_refresh"></a> Pour définir les options d'actualisation des données  
  
1.  Pointez vers un rapport de la bibliothèque.  
  
2.  Cliquez sur la flèche vers le bas et sélectionnez **Gérer les options de traitement**.  
  
3.  Dans **Options d'actualisation des données**, cliquez sur **Utiliser les données d'instantanés**. Si le message « Ce rapport ne peut pas être exécuté à partir d'un instantané parce qu'une ou plusieurs des informations d'identification des sources de données ne sont pas stockées » s'affiche, le rapport n'est pas configuré pour être exécuté sans assistance. Vous devez donc modifier les sources de données pour qu'elles utilisent les informations d'identification stockées avant de définir cette option.  
  
4.  Dans **Options d'instantanés des données**, sélectionnez **Planifier le traitement des données**.  
  
5.  Sélectionnez **Suivant une planification partagée** si vous disposez d'une planification partagée existante que vous pouvez utiliser ; sinon, cliquez sur **Suivant une planification personnalisée**, puis sur **Configurer**.  
  
6.  Sélectionnez la fréquence, la planification et les dates de début et de fin, puis cliquez sur **OK**.  
  
7.  Dans **Options d'instantanés des données**, sélectionnez **Créer ou mettre à jour l'instantané lorsque cette page est enregistrée** si vous souhaitez créer immédiatement les données d'instantané à utiliser avec le rapport sans attendre le traitement planifié des données.  
  
##  <a name="bkmk_set_report_caching"></a> Pour définir les options de mise en cache de rapport  
  
1.  Pointez vers un rapport de la bibliothèque.  
  
2.  Cliquez sur la flèche vers le bas et sélectionnez **Gérer les options de traitement**.  
  
3.  Dans **Options d'actualisation des données**, cliquez sur **Utiliser les données en cache**. Si le message « Ce rapport ne peut pas être mis en cache parce qu'une ou plusieurs informations d'identification des sources de données ne sont pas stockées » s'affiche, le rapport n'est pas configuré pour être exécuté sans assistance. Avant de définir cette option, vous devez donc modifier les sources de données pour qu'elles utilisent les informations d'identification stockées.  
  
4.  Dans **Options de cache**, spécifiez comment le cache expirera :  
  
    -   Entrez le nombre de minutes avant l'expiration du cache.  
  
    -   Utilisez une planification partagée pour effacer le cache à des instants spécifiés dans la planification.  
  
    -   Créez une planification personnalisée pour effacer le cache à un instant que vous spécifiez.  
  
##  <a name="bkmk_set_processing"></a> Pour définir des délais d'expiration de traitement  
  
1.  Pointez vers un rapport de la bibliothèque.  
  
2.  Cliquez sur la flèche vers le bas et sélectionnez **Gérer les options de traitement**.  
  
3.  Dans **Délai de traitement**, sélectionnez **Utiliser le paramètre par défaut de site** si vous voulez utiliser la valeur spécifiée au niveau du serveur de rapports. Sinon, sélectionnez **Ne pas spécifier de délai d’exécution lors du traitement du rapport** ou **Limiter le traitement des rapports (en secondes)** pour remplacer cette valeur par un délai d’expiration différent ou par aucun délai d’expiration.  
  
##  <a name="bkmk_set_report_history"></a> Pour définir les options et limites de l'historique de rapport  
  
1.  Pointez vers un rapport de la bibliothèque.  
  
2.  Cliquez sur la flèche vers le bas et sélectionnez **Gérer les options de traitement**.  
  
3.  Dans **Options des instantanés d'historique**, spécifiez comment et quand le traitement des données a lieu et est enregistré.  
  
4.  Dans **Limites des instantanés d'historique**, sélectionnez **Utiliser le paramètre par défaut de site** si vous voulez utiliser la valeur spécifiée au niveau du serveur de rapports. Sinon, sélectionnez **Ne pas limiter le nombre d'instantanés** ou **Limiter le nombre d'instantanés à** pour spécifier une valeur personnalisée.  
  
##  <a name="bkmk_set_database_timeout"></a> Définir le délai d'attente de base de données  
  
1.  Utilisez Windows PowerShell pour définir le délai d'attente de base de données sur un serveur de rapports SharePoint. Pour plus d'informations, consultez la section sur l'obtention et la définition des propriétés de base de données de l'application Reporting Service dans l'article [PowerShell cmdlets for Reporting Services SharePoint Mode](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Définir les propriétés de traitement d'un rapport](../../reporting-services/report-server/set-report-processing-properties.md)   
 [Mise en cache de rapports &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md)   
 [Définition des valeurs de délai d’attente pour le traitement d’un rapport et d’un dataset partagé &#40;SSRS&#41;](../../reporting-services/report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)  
  
  
