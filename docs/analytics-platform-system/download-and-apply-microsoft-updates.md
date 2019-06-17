---
title: Télécharger les mises à jour de Microsoft - Analytique Platform System | Microsoft Docs
description: Cette rubrique explique comment télécharger des mises à jour à partir du catalogue Microsoft Update pour Windows Server Update Services (WSUS) et appliquer ces mises à jour vers les serveurs d’appliance Analytique Platform System. Microsoft Update installera toutes les mises à jour applicables pour Windows et SQL Server. WSUS est installé sur l’ordinateur virtuel VMM de l’appliance.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: d71a6ddc965b422f0f96f40788352213501b4db2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63042309"
---
# <a name="download-and-apply-microsoft-updates-for-analytics-platform-system"></a>Téléchargez et appliquez les mises à jour Microsoft pour système de plateforme d’Analytique
Cette rubrique explique comment télécharger des mises à jour à partir du catalogue Microsoft Update pour Windows Server Update Services (WSUS) et appliquer ces mises à jour vers les serveurs d’appliance Analytique Platform System. Microsoft Update installera toutes les mises à jour applicables pour Windows et SQL Server. WSUS est installé sur l’ordinateur virtuel VMM de l’appliance.  
  
## <a name="TOP"></a>Avant de commencer  
  
> [!WARNING]  
> N’essayez pas d’appliquer les mises à jour si votre appliance ou n’importe quel composant de l’appliance est arrêté ou dans un état de pointage. Dans ce cas, contactez le support pour obtenir une assistance.  
>   
> N’appliquez pas de Microsoft Updates tandis que l’appliance est en cours d’utilisation. Mise à jour peut entraîner des nœuds d’appliance à redémarrer. Les mises à jour doivent être appliquées pendant une fenêtre de maintenance lors de l’appliance n’est pas utilisée.  
  
### <a name="prerequisites"></a>Prérequis  
Avant d’effectuer ces étapes, vous devez :  
  
-   Configurer WSUS sur votre appliance en suivant les instructions dans [configurer Windows Server Update Services &#40;WSUS&#41; &#40;Analytique Platform System&#41;](configure-windows-server-update-services-wsus.md).  
  
-   Connaissances une administrateur de domaine Fabric compte d’informations de connexion.  
  
-   Avoir une connexion avec des autorisations pour accéder à la Console d’administration Analytique Platform System et afficher des informations d’état appliance.  
  
-   Dans la plupart des cas, WSUS doit accéder aux serveurs en dehors de l’appliance. Pour prendre en charge ce scénario d’utilisation du système de plateforme Analytique DNS peut être configuré pour prendre en charge d’un redirecteur de nom externe qui autorise les hôtes de système de plateforme d’Analytique et les Machines virtuelles (VM) à utiliser les serveurs DNS externes pour résoudre les noms en dehors de la appliance. Pour plus d’informations, consultez [utiliser un redirecteur DNS pour résoudre les noms DNS Non-Appliance &#40;Analytique Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
## <a name="bkmk_ImportUpdates"></a>Pour télécharger et appliquer des mises à jour Microsoft  
  
#### <a name="verify-the-appliance-state-indicators"></a>Vérifiez les indicateurs d’état appliance  
  
1.  Ouvrez la Console d’administration et accédez à la page d’état de l’Appliance. Pour plus d’informations, consultez [surveiller l’Appliance à l’aide de la Console d’administration &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
2.  Vérifiez les indicateurs d’état pour tous les nœuds sur l’état de l’Appliance.  
  
    -   Il est possible de poursuivre vert ou indicateurs de NA.  
  
    -   Évaluer les erreurs d’avertissement (jaune) non critiques. Dans certains cas des messages d’avertissement ne bloquent pas les mises à jour. S’il existe une erreur de volume de disque non critiques qui n’est pas sur le lecteur C:\, vous pouvez passer à l’étape suivante avant de résoudre l’erreur de volume de disque.  
  
    -   La plupart des indicateurs rouges doivent être résolues avant de continuer. S’il existe des défaillances de disque, utilisez la page des alertes de la Console Administrateur vérifier que pas plus d’une défaillance de disque au sein de chaque serveur ou de la baie de SAN. En cas de défaillance de disque ne plusieurs au sein de chaque serveur ou de la baie de SAN, vous pouvez passer à l’étape suivante avant de corriger les défaillances de disque. Veillez à contacter le support Microsoft pour résoudre les défaillances de disque dès que possible.  
  
#### <a name="synchronize-the-wsus-server"></a>Synchroniser le serveur WSUS  
  
1.  Ouvrez une session en tant qu’un administrateur de domaine l’ordinateur virtuel VMM.  
  
2.  Dans le **tableau de bord Gestionnaire de serveur**, dans le **outils** menu, cliquez sur **Windows Server Update Services** (**wsus.msc**).  
  
3.  Dans la Console d’administration WSUS, cliquez sur **synchronisations**.  
  
4.  Si la synchronisation n’est pas en cours d’exécution, cliquez sur **synchroniser maintenant** dans le volet droit. Dans le volet inférieur, il y aura un état de synchronisation. Attendez que la synchronisation soit terminée.  
  
#### <a name="approve-microsoft-updates-in-wsus"></a>Approuver les mises à jour dans WSUS  
  
1.  Dans le volet gauche, de la console WSUS, cliquez sur **toutes les mises à jour**.  
  
2.  Dans le **toutes les mises à jour** volet, cliquez sur le **approbation** menu déroulant, définissez **approbation** à **toutes sauf refusées**. Cliquez sur le **état** menu déroulant, définissez **état** à **n’importe quel**. Cliquez sur **Actualiser**.  
  
    Avec le bouton droit le **titre** colonne, puis sélectionnez **état du fichier** pour vérifier l’état du fichier une fois le téléchargement terminé.  
  
    Vous pouvez également sélectionner **mises à jour critiques** ou **mises à jour de sécurité** dans les gauche volet et affichage mises à jour disponibles pour ces catégories.  
  
    ![Sélectionnez toutes les mises à jour et modifiez un état. ](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectAllUpdates.png "SQL_Server_PDW_WSUSSelectAllUpdates")  
  
3.  Sélectionnez toutes les mises à jour, puis cliquez sur le **approuver** lien dans le volet droit.  
  
    Vous pouvez également cliquez sur les mises à jour sélectionnées, puis cliquez sur **approuver**. Vous pouvez être invité à accepter le « contrat de licence Microsoft ». Dans ce cas, cliquez sur **J’accepte** dans la fenêtre pour continuer.  
  
    ![Sélectionnez toutes les mises à jour applicables et cliquer sur Approuver. ](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprove.png "SQL_Server_PDW_WSUSSelectApprove")  
  
4.  Sélectionnez le groupe de serveurs appliance que vous avez créé dans [configurer Windows Server Update Services &#40;WSUS&#41; &#40;Analytique Platform System&#41;](configure-windows-server-update-services-wsus.md).  
  
5.  Cliquez sur **approuvée pour l’installation**, puis cliquez sur **OK**.  
  
    ![Approuver les mises à jour pour votre groupe d’ordinateurs. ](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprovalType.png "SQL_Server_PDW_WSUSSelectApprovalType")  
  
6.  Dans le **progression de l’approbation** boîte de dialogue, lorsque le processus d’approbation est terminé, cliquez sur **fermer**.  
  
    ![Fermer la fenêtre lorsque les mises à jour sont approuvées. ](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSCloseApprovalProgressWindow.png "SQL_Server_PDW_WSUSCloseApprovalProgressWindow")  
  
#### <a name="verify-that-the-updates-are-in-wsus"></a>Vérifiez que les mises à jour WSUS  
  
-  Vérifiez l’état de toutes les mises à jour du fichier. Chaque fichier doit avoir une icône de flèche verte à gauche du titre. Cela indique que le fichier est prêt pour l’installation.  
  
    ![État du fichier est réussi](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUS_File_Status.png "SQL_Server_PDW_WSUS_File_Status")  
  
    Avant d’installer les mises à jour, assurez-vous qu’ils sont tous téléchargé et disponible dans la console WSUS.  
  
#### <a name="to-verify-that-all-updates-are-downloaded"></a>Pour vérifier que toutes les mises à jour sont téléchargées.  
  
-  Vérifier le **état du téléchargement de** des mises à jour dans la console WSUS, comme illustré dans la capture d’écran suivante. Vérifiez que **mises à jour nécessitant des fichiers** est égal à 0 pour confirmer que toutes les mises à jour sont téléchargées. Si ce nombre est supérieur à zéro, vous devrez peut-être revenir en arrière et approuver les mises à jour supplémentaires.  
  
    ![Vérifiez que toutes les mises à jour sont téléchargées. ](./media/download-and-apply-microsoft-updates/SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG.png "SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG")  
  
#### <a name="apply-microsoft-updates"></a>Appliquer des mises à jour Microsoft  
  
1.  Avant de commencer, ouvrez le [surveiller l’Appliance à l’aide de la Console d’administration &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md), cliquez sur le **Appliance état** onglet et vérifiez que le  **Cluster** et **réseau** colonnes show vert (ou NA) pour tous les nœuds. Si toutes les alertes existent dans une de ces colonnes, l’appliance ne peut pas être en mesure d’installer les mises à jour correctement. Résoudre toutes les alertes existantes dans le **Cluster** et **réseau** colonnes avant de continuer.  
  
2.  Ouvrez une session sur le _< nom_domaine >_ **-HST01** nœud en tant que l’administrateur de domaine Fabric.  
  
3.  Pour appliquer toutes les mises à jour approuvées pour WSUS, exécutez le programme de mise à jour. Consultez [exécuter le programme de mise à jour](#RunUpdateWizard) ci-dessous pour obtenir des instructions.  
  
#### <a name="verify-the-updates-on-all-nodes"></a>Vérifier les mises à jour sur tous les nœuds  
  
1.  À partir du nœud VMM, lancez la Console d’administration WSUS. Cette application peut être trouvée sous **Démarrer**, **outils d’administration**, **Windows Server Update Services**.  
  
2.  Développez **ordinateurs**.  
  
3.  Développez **tous les ordinateurs**.  
  
4.  Sélectionnez le groupe de serveurs appliance que vous avez créé dans [configurer Windows Server Update Services &#40;WSUS&#41; &#40;Analytique Platform System&#41;](configure-windows-server-update-services-wsus.md).  
  
5.  Dans le **état** menu déroulant, sélectionnez **n’importe quel** et cliquez sur **Actualiser**.  
  
6.  Développez **mettre à jour des Services**, *<appliance name>* - VMM, **mises à jour**, **toutes les mises à jour**, où *<appliance name>* est le nom de votre appliance.  
  
7.  Dans le **toutes les mises à jour** ensemble de la fenêtre **approbation** à **toutes sauf refusées**.  
  
8.  Dans le **toutes les mises à jour** fenêtre, définissez **état** à **ont échoué ou nécessaires**.  
  
9. Cliquez sur **Actualiser**.  
  
10. Si **mises à jour nécessaires** est supérieur à zéro, contactez le support technique pour obtenir une assistance.  
  
#### <a name="ensure-there-are-no-critical-alerts-in-the-sql-server-pdw-admin-console"></a>Assurez-vous qu'il n’y aucune alerte critique dans la Console d’administration SQL Server PDW  
  
1.  Ouvrez la Console d’administration, cliquez sur l’onglet État de l’Appliance. Consultez [surveiller l’Appliance à l’aide de la Console d’administration &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).  
  
2.  Vérifiez que le **Cluster** et **réseau** colonnes show vert (ou NA) pour tous les nœuds. Si toutes les alertes existent dans une de ces colonnes, l’appliance ne peut pas être en mesure d’installer les mises à jour correctement. Contactez le support technique s’il existe des alertes critiques.  
  
## <a name="RunUpdateWizard"></a>Exécutez le programme de mise à jour  
Suivez ces instructions pour exécuter le programme de mise à jour de système de plateforme Analytique.  
  
> [!NOTE]  
> Le système WSUS est conçu pour exécuter en mode asynchrone peut prendre un certain temps s’appliquent pleinement toutes les mises à jour. Lancer une mise à jour une mise à jour des planifications, mais ne garantit pas l’activité de mise à jour immédiate.  
  
1.  Assurez-vous que vous êtes connecté au nœud HST01 en tant que l’administrateur de domaine Fabric.  
  
2.  Ouvrez une fenêtre d’invite de commandes et entrez les commandes suivantes. Remplacez *<parameter>* avec les informations désignées.  
  
**Pour exécuter la mise à jour de Microsoft :**  
  
```  
C:\pdwinst\media\setup.exe /action="MicrosoftUpdate" /DomainAdminPassword="<password>"  
```  
  
**Pour signaler l’état de Microsoft Update :**  
  
```  
C:\pdwinst\media\setup.exe /action="ReportMicrosoftUpdateClientStatus" /DomainAdminPassword="<password>"  
```  
  
## <a name="see-also"></a>Voir aussi  
[Désinstaller les mises à jour Microsoft &#40;Analytique Platform System&#41;](uninstall-microsoft-updates.md)  
[Appliquer des correctifs de système de plateforme Analytique &#40;Analytique Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
[Désinstallation de correctifs de système de plateforme Analytique &#40;Analytique Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Maintenance logicielle &#40;Analytique Platform System&#41;](software-servicing.md)  
  
