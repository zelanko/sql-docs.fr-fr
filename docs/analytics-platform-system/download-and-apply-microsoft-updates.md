---
title: Télécharger les mises à jour Microsoft
description: Cette rubrique explique comment télécharger des mises à jour à partir du catalogue Microsoft Update vers Windows Server Update Services (WSUS) et appliquer ces mises à jour aux serveurs d’appliances système Analytics Platform. Microsoft Update installera toutes les mises à jour applicables pour Windows et SQL Server. WSUS est installé sur la machine virtuelle VMM de l’appliance.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 2b24d55720d6db5997bfa85c2621f0e8d58c5f95
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401193"
---
# <a name="download-and-apply-microsoft-updates-for-analytics-platform-system"></a>Télécharger et appliquer des mises à jour Microsoft pour Analytics Platform System
Cette rubrique explique comment télécharger des mises à jour à partir du catalogue Microsoft Update vers Windows Server Update Services (WSUS) et appliquer ces mises à jour aux serveurs d’appliances système Analytics Platform. Microsoft Update installera toutes les mises à jour applicables pour Windows et SQL Server. WSUS est installé sur la machine virtuelle VMM de l’appliance.  
  
## <a name="before-you-begin"></a><a name="TOP"></a>Avant de commencer  
  
> [!WARNING]  
> N’essayez pas d’appliquer les mises à jour si votre appliance ou un composant de l’appareil est en panne ou dans un État basculé. Dans ce cas, contactez le support technique pour obtenir de l’aide.  
>   
> N’appliquez pas les mises à jour Microsoft lorsque l’appliance est en cours d’utilisation. L’application de mises à jour peut entraîner le redémarrage des nœuds de l’appliance. Les mises à jour doivent être appliquées au cours d’une fenêtre de maintenance lorsque l’appliance n’est pas utilisée.  
  
### <a name="prerequisites"></a>Prérequis  
Avant d’effectuer ces étapes, vous devez :  
  
-   Configurez WSUS sur votre appareil en suivant les instructions de la procédure de [configuration de Windows Server Update Services &#40;wsus&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md).  
  
-   Connaissance des informations de connexion du compte d’administrateur de domaine de l’infrastructure.  
  
-   Disposer d’une connexion disposant d’autorisations pour accéder à la console d’administration système Analytics Platform et afficher les informations d’état de l’appliance.  
  
-   Dans la plupart des cas, WSUS doit accéder aux serveurs en dehors de l’appliance. Pour prendre en charge ce scénario d’utilisation, le système DNS de la plateforme d’analyse peut être configuré pour prendre en charge un redirecteur de nom externe qui permettra aux ordinateurs hôtes du système de plateforme d’analyse et aux machines virtuelles d’utiliser des serveurs DNS externes pour résoudre les noms en dehors de l’appliance. Pour plus d’informations, consultez [utiliser un redirecteur DNS pour résoudre les noms DNS non-Appliance &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
## <a name="to-download-and-apply-microsoft-updates"></a><a name="bkmk_ImportUpdates"></a>Pour télécharger et appliquer des mises à jour Microsoft  
  
#### <a name="verify-the-appliance-state-indicators"></a>Vérifier les indicateurs d’état de l’appliance  
  
1.  Ouvrez la console d’administration et accédez à la page État de l’appliance. Pour plus d’informations, consultez [surveiller l’appliance à l’aide de la console d’administration &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
2.  Vérifiez les indicateurs d’état de tous les nœuds de l’état de l’appliance.  
  
    -   Il est possible de continuer en toute sécurité avec des indicateurs en vert ou en NA.  
  
    -   Évaluer les erreurs d’avertissement non critiques (jaunes). Dans certains cas, les messages d’avertissement ne bloquent pas les mises à jour. S’il y a une erreur de volume de disque non critique qui ne se trouve pas sur C:\ , vous pouvez passer à l’étape suivante avant de résoudre l’erreur de volume de disque.  
  
    -   La plupart des indicateurs rouges doivent être résolus avant de continuer. En cas de défaillances de disque, utilisez la page alertes de la console d’administration pour vérifier qu’il n’y a pas plus d’une défaillance de disque au sein de chaque serveur ou groupe SAN. S’il n’y a pas plus d’une défaillance de disque au sein de chaque serveur ou groupe SAN, vous pouvez passer à l’étape suivante avant de résoudre les défaillances de disque. Veillez à contacter le support Microsoft pour résoudre les défaillances de disque dès que possible.  
  
#### <a name="synchronize-the-wsus-server"></a>Synchroniser le serveur WSUS  
  
1.  Connectez-vous à la machine virtuelle VMM en tant qu’administrateur de domaine.  
  
2.  Dans le **tableau de bord gestionnaire de serveur**, dans le menu **Outils** , cliquez sur **Windows Server Update Services** (**WSUS. msc**).  
  
3.  Dans la console d’administration WSUS, cliquez sur **synchronisations**.  
  
4.  Si la synchronisation n’est pas en cours d’exécution, cliquez sur **Synchroniser maintenant** dans le volet droit. Dans le volet inférieur, il y aura un état de synchronisation. Attendez la fin de la synchronisation.  
  
#### <a name="approve-microsoft-updates-in-wsus"></a>Approuver les mises à jour Microsoft dans WSUS  
  
1.  Dans le volet gauche, dans la console WSUS, cliquez sur **toutes les mises à jour**.  
  
2.  Dans le volet **toutes les mises à jour** , cliquez sur le menu déroulant **approbation** , définissez **approbation** sur **tout sauf refusé**. Cliquez sur le menu déroulant **Status (État** ), puis définissez **Status** sur **Any (tout**). Cliquez sur **Actualiser**.  
  
    Cliquez avec le bouton droit sur la colonne **titre** et sélectionnez **État du fichier** pour vérifier l’état du fichier une fois le téléchargement terminé.  
  
    Vous pouvez également sélectionner mises à jour **critiques** ou **mises à jour de sécurité** dans le volet gauche et afficher les mises à jour disponibles pour ces catégories.  
  
    ![Sélectionner toutes les mises à jour et modifier l'état en N'importe quel](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectAllUpdates.png "SQL_Server_PDW_WSUSSelectAllUpdates")  
  
3.  Sélectionnez toutes les mises à jour, puis cliquez sur le lien **approuver** dans le volet droit.  
  
    Vous pouvez également cliquer avec le bouton droit sur les mises à jour sélectionnées, puis cliquer sur **approuver**. Vous pouvez être invité à accepter les termes du contrat de licence logiciel Microsoft. Dans ce cas, cliquez sur **J’accepte** dans la fenêtre pour continuer.  
  
    ![Sélectionner toutes les mises à jour applicables et cliquer sur Approuver.](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprove.png "SQL_Server_PDW_WSUSSelectApprove")  
  
4.  Sélectionnez le groupe de serveurs d’appliance que vous avez créé dans [configurer Windows Server Update Services &#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md).  
  
5.  Cliquez sur **Approuvée pour l’installation**, puis sur **OK**.  
  
    ![Approuver les mises à jour pour le groupe d'ordinateurs.](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprovalType.png "SQL_Server_PDW_WSUSSelectApprovalType")  
  
6.  Dans la boîte de dialogue progression de l' **approbation** , lorsque le processus d’approbation est terminé, cliquez sur **Fermer**.  
  
    ![Fermer la fenêtre quand des mises à jour sont approuvées.](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSCloseApprovalProgressWindow.png "SQL_Server_PDW_WSUSCloseApprovalProgressWindow")  
  
#### <a name="verify-that-the-updates-are-in-wsus"></a>Vérifier que les mises à jour sont dans WSUS  
  
-  Vérifiez l’état des fichiers de toutes les mises à jour. Chaque fichier doit comporter une icône représentant une flèche verte à gauche du titre. Cela indique que le fichier est prêt pour l’installation.  
  
    ![L'état du fichier est Réussi](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUS_File_Status.png "SQL_Server_PDW_WSUS_File_Status")  
  
    Avant d’installer les mises à jour, assurez-vous qu’elles sont téléchargées et disponibles dans la console WSUS.  
  
#### <a name="to-verify-that-all-updates-are-downloaded"></a>Pour vérifier que toutes les mises à jour sont téléchargées  
  
-  Vérifiez l' **État de téléchargement** des mises à jour dans la console WSUS, comme indiqué dans la capture d’écran suivante. Vérifiez que les **mises à jour nécessitant des fichiers** sont égales à 0 pour confirmer que toutes les mises à jour sont téléchargées. Si ce nombre est supérieur à zéro, vous devrez peut-être revenir en arrière et approuver des mises à jour supplémentaires.  
  
    ![Vérifier que toutes les mises à jour sont téléchargées.](./media/download-and-apply-microsoft-updates/SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG.png "SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG")  
  
#### <a name="apply-microsoft-updates"></a>Appliquer les mises à jour Microsoft  
  
1.  Avant de commencer, ouvrez l' [application analyser l’appliance à l’aide de la console d’administration de &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md), cliquez sur l’onglet **État** de l’appliance, puis vérifiez que les colonnes **cluster** et **réseau** affichent le vert (ou na) pour tous les nœuds. Si des alertes se trouvent dans l’une de ces colonnes, l’appliance peut ne pas être en mesure d’installer les mises à jour correctement. Traitez toutes les alertes existantes dans les colonnes de **cluster** et de **réseau** avant de continuer.  
  
2.  Connectez-vous au nœud _<domain_name>_ **-HST01** en tant qu’administrateur de domaine de l’infrastructure.  
  
3.  Pour appliquer toutes les mises à jour approuvées pour WSUS, exécutez le programme de mise à jour. Pour obtenir des instructions, consultez [exécuter le programme de mise à jour](#RunUpdateWizard) ci-dessous.  
  
#### <a name="verify-the-updates-on-all-nodes"></a>Vérifier les mises à jour sur tous les nœuds  
  
1.  À partir du nœud VMM, lancez la console d’administration WSUS. Cette application se trouve sous **Démarrer**, **Outils d’administration**, **Windows Server Update Services**.  
  
2.  Développez **ordinateurs**.  
  
3.  Développez **tous les ordinateurs**.  
  
4.  Sélectionnez le groupe de serveurs d’appliance que vous avez créé dans [configurer Windows Server Update Services &#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md).  
  
5.  Dans le menu déroulant **État** , sélectionnez **n’importe laquelle** , puis cliquez sur **Actualiser**.  
  
6.  Développez Services de *<appliance name>* **mise à jour**,-VMM, **mises à**jour, **toutes les mises à jour**, où *<appliance name>* est le nom de votre appliance.  
  
7.  Dans la fenêtre **toutes les mises à jour** , définissez **approbation** sur **tout sauf refusée**.  
  
8.  Dans la fenêtre **toutes les mises à jour** , définissez **État** sur **échec ou requis**.  
  
9. Cliquez sur **Actualiser**.  
  
10. Si les **mises à jour nécessaires** sont supérieures à zéro, contactez le support technique pour obtenir de l’aide.  
  
#### <a name="ensure-there-are-no-critical-alerts-in-the-sql-server-pdw-admin-console"></a>Vérifier qu’il n’y a pas d’alertes critiques dans la console d’administration SQL Server PDW  
  
1.  Ouvrez la console d’administration, puis cliquez sur l’onglet État de l’appliance. Consultez [surveiller l’appliance à l’aide de la console d’administration &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).  
  
2.  Vérifiez que les colonnes **cluster** et **réseau** affichent le vert (ou na) pour tous les nœuds. Si des alertes se trouvent dans l’une de ces colonnes, l’appliance peut ne pas être en mesure d’installer les mises à jour correctement. Contactez le support technique s’il existe des alertes critiques.  
  
## <a name="run-the-update-program"></a><a name="RunUpdateWizard"></a>Exécuter le programme de mise à jour  
Suivez ces instructions pour exécuter le programme de mise à jour du système Analytics Platform.  
  
> [!NOTE]  
> Le système WSUS est conçu pour s’exécuter de façon asynchrone et peut prendre un certain temps pour appliquer entièrement toutes les mises à jour. Le lancement d’une mise à jour planifie une mise à jour mais ne garantit pas l’activité immédiate des mises à jour.  
  
1.  Vérifiez que vous êtes connecté au nœud HST01 en tant qu’administrateur de domaine de l’infrastructure.  
  
2.  Ouvrez une fenêtre d’invite de commandes et entrez les commandes suivantes. Remplacez *<parameter>* par les informations spécifiées.  
  
**Pour exécuter l’Microsoft Update :**  
  
```  
C:\pdwinst\media\setup.exe /action="MicrosoftUpdate" /DomainAdminPassword="<password>"  
```  
  
**Pour signaler l’état du Microsoft Update :**  
  
```  
C:\pdwinst\media\setup.exe /action="ReportMicrosoftUpdateClientStatus" /DomainAdminPassword="<password>"  
```  
  
## <a name="see-also"></a>Voir aussi  
[Désinstallez les mises à jour Microsoft &#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
[Appliquer des correctifs logiciels Analytics Platform System &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
[Désinstallation des correctifs du système de plateforme Analytics &#40;Analytics&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Maintenance logicielle &#40;système de plateforme Analytics&#41;](software-servicing.md)  
  
