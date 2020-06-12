---
title: Règles d’intégrité PowerPivot-configurer | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a01e63e6-97dc-43e5-ad12-ae6580afc606
author: minewiskan
ms.author: owend
ms.openlocfilehash: 216721a187d86e56154d5d25c5e3174d231f7f36
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547541"
---
# <a name="powerpivot-health-rules---configure"></a>Règles d'intégrité de PowerPivot - Configurer
  PowerPivot pour SharePoint inclut des règles d'intégrité SharePoint qui vous aident à analyser et à résoudre les problèmes de disponibilité et de configuration du serveur. Les règles d'intégrité qui s'appliquent à PowerPivot pour SharePoint apparaissent dans la page Vérifier les définitions de règles.  
  
 Les règles d'intégrité permettent la détection anticipée des problèmes de serveur susceptibles de provoquer des interruptions de service. PowerPivot pour SharePoint fournit plusieurs règles pour vous aider à identifier et résoudre les problèmes avant qu'ils ne touchent vos utilisateurs. Vous pouvez personnaliser beaucoup de ces règles pour les adapter aux besoins uniques de votre déploiement. Par exemple, si vous souhaitez disposer de plus de temps pour traiter les avertissements relatifs à l'espace disque, vous pouvez augmenter le pourcentage d'espace disque disponible de 5 % à 10 % afin de recevoir l'avertissement plus tôt.  
  
 Les règles qui peuvent être personnalisées sont celles qui surveillent la consommation des ressources ou la disponibilité du serveur. La personnalisation est utile dans ce cas parce que la capacité du système sous-jacent varie fortement selon les topologies de serveur et de déploiement. Par opposition, aucune personnalisation n'est possible pour les règles qui identifient la configuration du serveur ou les problèmes de sécurité. Ces règles doivent être appliquée uniformément sur toutes les installations.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|  
  
 **Remarque :** les paramètres des règles d'intégrité sont configurés séparément pour l'instance de SQL Server Analysis Services et l'application de service PowerPivot. Suivez les instructions de cette rubrique pour configurer des règles d'intégrité pour chaque service. Pour un déploiement SharePoint 2013, [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] utilise uniquement l'application de service. Par conséquent, [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] installe différents jeux de règles d'intégrité pour différentes versions de SharePoint. Consultez la colonne « version » dans la rubrique [référence des règles d’intégrité &#40;PowerPivot pour SharePoint&#41;](health-rules-reference-power-pivot-for-sharepoint.md), ou exécutez la commande Windows PowerShell suivante pour voir les règles installées.  
  
```powershell
Get-SPHealthAnalysisRule | Select name, enabled, summary | Where {$_.summary -like "*power*"}  | Format-Table -Property * -AutoSize | Out-Default  
```  
  
 **Dans cette rubrique :**  
  
 [Afficher les règles d'intégrité PowerPivot](#bkmk_view)  
  
 [Configurer les règles d'intégrité utilisées pour évaluer la stabilité du serveur (SQL Server Analysis Services)](#bkmk_HR_SSAS)  
  
 [Configurer les règles d'intégrité utilisées pour évaluer la stabilité de l'application (Application de service PowerPivot)](#bkmk_evaluate_application_stability)  
  
## <a name="prerequisites"></a>Prérequis  
 Vous devez être administrateur de l'application de service pour modifier les propriétés de configuration de l'instance d'Analysis Services et de l'application de service PowerPivot.  
  
##  <a name="view-powerpivot-health-rules"></a><a name="bkmk_view"></a>Afficher les règles d’intégrité PowerPivot  
  
1.  Dans l'Administration centrale de SharePoint, cliquez sur **Analyse**, puis dans la section **Analyseur d’intégrité** , cliquez sur **Vérifier les définitions de règles**.  
  
2.  Dans la section de configuration, recherchez les règles qui ont le préfixe **PowerPivot :** . Toutes les règles d'intégrité connexes à PowerPivot ont ce préfixe pour vous aider à les distinguer des règles SharePoint intégrées.  
  
 Ces règles s'afficheront dans la page **Examiner les problèmes et solutions** lorsque des problèmes sont détectés.  
  
 Si vous soupçonnez un problème et souhaitez vérifier cela immédiatement, vous pouvez exécuter manuellement une vérification de la règle pour déterminer si un problème existe.  
  
 Pour ce faire, cliquez sur la règle pour ouvrir sa définition, puis cliquez sur **Exécuter maintenant** dans le ruban. Cliquez sur **Fermer** pour revenir à la page **Examiner les problèmes et solutions** et afficher le rapport. Si la règle a détecté un problème, un avertissement ou une erreur sera signalé sur la page. Dans certains cas, l'affichage de l'erreur ou de l'avertissement peut prendre quelques minutes.  
  
##  <a name="configure-health-rules-used-to-evaluate-server-stability-sql-server-analysis-services"></a><a name="bkmk_HR_SSAS"></a>Configurer les règles d’intégrité utilisées pour évaluer la stabilité du serveur (SQL Server Analysis Services)  
 L'instance d'Analysis Services inclut des règles d'intégrité qui détectent des problèmes au niveau du système (UC, mémoire et espace disque utilisé pour la mise en cache). Utilisez les instructions suivantes pour modifier les seuils qui déclenchent des règles d'intégrité spécifiques.  
  
1.  Dans l'Administration centrale de SharePoint, cliquez sur **Gérer les services sur le serveur** dans la section **Paramètres système**.  
  
2.  En haut de la page, sélectionnez le serveur dans votre batterie de serveurs SharePoint dotée d'une instance d'Analysis Services (dans l'illustration suivante, le nom du serveur est AW-SRV033). **SQL Server Analysis Services** apparaît dans la liste des services.  
  
     ![Capture d'écran de la page Gérer les services sur le serveur](../media/ssas-centraladmin-servicesonserver.gif "Capture d'écran de la page Gérer les services sur le serveur")  
  
3.  Cliquez sur **SQL Server Analysis Services**.  
  
4.  Dans les pages de propriétés du service, dans Paramètres de règle d'intégrité, modifiez les paramètres suivants :  
  
     Allocation de ressources processeur insuffisante (la valeur par défaut est 80 %)  
     Cette règle d'intégrité est déclenchée si les ressources processeur utilisées par le processus serveur d'Analysis Services (msmdsrv.exe) sont supérieures ou égales à 80 % pendant une période de 4 heures (comme spécifié par le paramètre Intervalle de collecte des données).  
  
     Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : Analysis Services ne dispose pas de suffisamment de ressources processeur pour effectuer les opérations demandées.**  
  
     Ressources processeur insuffisantes sur le système (la valeur par défaut est 90 %)  
     Cette règle d'intégrité est déclenchée si les ressources processeur pour le serveur sont inférieures ou égales à 90 % pendant une période de 4 heures (comme spécifié via le paramètre Intervalle de collecte des données). L'utilisation générale de l'UC est mesurée dans le cadre de l'algorithme d'équilibrage de charge basé sur l'intégrité qui surveille l'utilisation de l'UC pour mesurer l'intégrité du serveur.  
  
     Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : l'utilisation globale du processeur est trop élevée.**  
  
     Seuil de mémoire insuffisante (la valeur par défaut est 5 %)  
     Sur un serveur d'applications SharePoint, une instance de SQL Server Analysis Services doit toujours avoir une quantité minimale de mémoire en réserve, toujours inutilisée. Étant donné que le fonctionnement du serveur est lié à la mémoire pour la plupart de ses opérations, celui-ci s'exécute mieux s'il n'atteint pas complètement la limite supérieure. Les 5 % de mémoire inutilisée sont calculés sous forme de pourcentage de la mémoire allouée à Analysis Services. Par exemple, si vous avez 200 Go de mémoire totale et qu'Analysis Services en utilise 80 % (soit 160 Go), les 5 % de mémoire inutilisée correspondent à 5 % de 160 Go (soit 8 Go).  
  
     Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : Analysis Services ne dispose pas de suffisamment de mémoire pour effectuer les opérations demandées.**  
  
     Nombre maximal de connexions (la valeur par défaut est 100)  
     Cette règle d'intégrité est déclenchée si le nombre de connexions à l'instance d'Analysis Services est supérieur ou égal à 100 connexions pendant une période de 4 heures (comme spécifié via le paramètre Intervalle de collecte des données). Cette valeur par défaut est arbitraire (elle n'est pas basée sur les spécifications matérielles de votre serveur ou sur l'activité des utilisateurs), vous pouvez donc augmenter ou diminuer la valeur en fonction de la capacité du serveur et de l'activité des utilisateurs dans votre environnement.  
  
     Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : le nombre élevé de connexions indique que davantage de serveurs devraient être déployés afin de pouvoir gérer la charge actuelle.**  
  
     Espace disque insuffisant (la valeur par défaut est 5 %)  
     L'espace disque est utilisé pour mettre en cache les données PowerPivot chaque fois qu'une base de données est demandée. Cette règle vous permet de savoir quand l'espace disque est trop faible. Par défaut, cette règle d'intégrité est déclenchée lorsque l'espace disque est inférieur à 5 % sur le lecteur de disque où se trouve le dossier de sauvegarde. Pour plus d’informations sur l’utilisation des disques, consultez [configurer l’utilisation de l’espace disque &#40;PowerPivot pour SharePoint&#41;](configure-disk-space-usage-power-pivot-for-sharepoint.md).  
  
     Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : il n'y a presque plus d'espace disponible sur le lecteur sur lequel se trouvent les données PowerPivot mises en cache.**  
  
     Intervalle de collecte des données (en heures)  
     Vous pouvez spécifier la période de collecte de données prise en compte pour calculer les valeurs utilisées pour déclencher des règles d'intégrité. Bien que le système soit surveillé en permanence, les seuils utilisés pour déclencher des avertissements de règle d'intégrité sont calculés à l'aide de données qui ont été générées pendant un intervalle prédéfini. L'intervalle par défaut est de 4 heures. Le serveur récupère les données système et d'utilisation collectées au cours des 4 heures précédentes pour évaluer le nombre de connexions utilisateur, l'utilisation de l'espace disque et les taux d'utilisation de l'UC et de la mémoire.  
  
##  <a name="configure-health-rules-used-to-evaluate-application-stability-powerpivot-service-application"></a><a name="bkmk_evaluate_application_stability"></a>Configurer les règles d’intégrité utilisées pour évaluer la stabilité de l’application (application de service PowerPivot)  
  
1.  Dans administration centrale, dans gestion des applications, cliquez sur **gérer les applications de service**.  
  
2.  Dans la page Applications de service, cliquez sur **Application de service PowerPivot par défaut**.  
  
     ![Capture d'écran de la page Gérer l'application de service](../media/ssas-centraladmin-app.gif "Capture d'écran de la page Gérer l'application de service")  
  
3.  Le Tableau de bord de gestion PowerPivot apparaît. Cliquez sur **Configurer les paramètres d'application de service** dans la liste **Actions** pour ouvrir la page des paramètres d'application de service.  
  
     ![Capture d'écran du tableau de bord, et plus particulièrement de la liste Actions](../media/ssas-centraladmin-actionslist.gif "Capture d'écran du tableau de bord, et plus particulièrement de la liste Actions")  
  
4.  Dans les paramètres de la règle d'intégrité modifiez les paramètres suivants :  
  
     Rapport chargements/connexions (la valeur par défaut est 20 %)  
     Cette règle d'intégrité est déclenchée si le nombre d'événements de chargement est élevé par rapport au nombre d'événements de connexion, et signale que le serveur est peut-être en train de décharger trop rapidement des bases de données, ou que les paramètres de réduction du cache sont trop stricts.  
  
     Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : le taux d'événements de chargement par rapport aux connexions est trop élevé.**  
  
     Intervalle de collecte des données (la valeur par défaut est 4 heures)  
     Vous pouvez spécifier la période de collecte de données prise en compte pour calculer les valeurs utilisées pour déclencher des règles d'intégrité. Bien que le système soit surveillé en permanence, les seuils utilisés pour déclencher des avertissements de règle d'intégrité sont calculés à l'aide de données qui ont été générées pendant un intervalle prédéfini. L'intervalle par défaut est de 4 heures. Le serveur récupère les données système et d'utilisation collectées au cours des 4 heures précédentes pour évaluer le rapport chargement/connexion.  
  
     Recherche les mises à jour du fichier de gestion Dashboard.xlsx PowerPivot (la valeur par défaut est 5 jours)  
     Le fichier de la gestion Dashboard.xlsx PowerPivot est une source de données utilisée par les rapports du Tableau de bord de gestion PowerPivot. Dans une configuration de serveur par défaut, le fichier .xlsx est actualisé quotidiennement, à l'aide des données d'utilisation collectées par SharePoint et le service système PowerPivot. Si le fichier n'est pas mis à jour, une règle d'intégrité le signale comme un problème. Par défaut, la règle est déclenchée si l'horodateur du fichier n'a pas changé pendant 5 jours.  
  
     Pour plus d’informations sur la collecte des données d’utilisation, consultez [configurer la collecte des données d’utilisation pour &#40;PowerPivot pour SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md).  
  
     Ce paramètre de configuration correspond à la définition de règle suivante sur la page **Examiner les problèmes et solutions** : **PowerPivot : les données d'utilisation ne sont pas mises à jour à la fréquence prévue.**  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer l’utilisation de l’espace disque &#40;PowerPivot pour SharePoint&#41;](configure-disk-space-usage-power-pivot-for-sharepoint.md)   
 [Tableau de bord de gestion PowerPivot et données d’utilisation](power-pivot-management-dashboard-and-usage-data.md)  
