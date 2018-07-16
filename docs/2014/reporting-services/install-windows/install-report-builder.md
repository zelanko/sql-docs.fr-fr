---
title: Installer la Version autonome du Générateur de rapports (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6b2291bb-1d20-4d08-81cb-a16dd8e01faf
caps.latest.revision: 10
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 0fb9e6b43faf8b3ff7e0b91ccb500b94547436aa
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37305079"
---
# <a name="install-the-stand-alone-version-of-report-builder-report-builder"></a>Installer la version autonome du Générateur de rapports (Générateur de rapports)
  Vous pouvez installer le Générateur de rapports à partir de la [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] feature pack via le [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=168472) ou un emplacement tel que les dossiers publics auxquels le ReportBuilder3_x86.msi, le Package du programme d’installation de Windows pour le Générateur de rapports, a été téléchargé.  
  
 Vous pouvez également effectuer une installation du Générateur de rapports à partir de la ligne de commande et spécifier des arguments afin de personnaliser l'installation. Outre les paramètres MSI standard intrinsèques, vous pouvez utiliser les paramètres personnalisés fournis par le Générateur de rapports : RBINSTALLDIR et REPORTSERVERURL. RBINSTALLDIR spécifie le dossier d'installation racine pour le Générateur de rapports. REPORTSERVERURL spécifie le serveur de rapports par défaut utilisé par le Générateur de rapports pour enregistrer des rapports.  
  
 Si vous souhaitez effectuer une installation totalement sans assistance, sans aucune interaction avec l’interface utilisateur, spécifiez l’option **/quiet** . Par défaut, l'indicateur d'option quiet supprime les erreurs d'installation. Il est par conséquent recommandé d’inclure l’option **/l** , qui spécifie l’enregistrement dans le journal, lorsque vous utilisez l’option quiet.  
  
> [!IMPORTANT]  
>  Les fonctionnalités de sécurité de Windows Vista et Windows 7 requièrent des autorisations élevées pour exécuter des opérations en ligne de commande ; par conséquent, vous êtes invité à confirmer que vous avez l'autorisation d'exécuter la ligne de commande. Il ne s'agit pas d'une installation sans assistance. Pour effectuer une installation sans assistance, vous devez exécuter la ligne de commande en tant qu'administrateur.  
  
### <a name="to-install-report-builder-from-the-download-site"></a>Pour installer le Générateur de rapports à partir du site de téléchargement  
  
1.  Accédez à [Générateur de rapports Microsoft SQL Server 2012](http://go.microsoft.com/fwlink/?LinkID=219138) et recherchez la section Générateur de rapports de la page Web.  
  
2.  Cliquez sur **X86 Package**.  
  
3.  Dans le **téléchargement de fichier** boîte de dialogue, cliquez sur **exécuter**.  
  
    > [!IMPORTANT]  
    >  Téléchargez uniquement les fichiers provenant de sources fiables.  
  
4.  Dans la boîte de dialogue Internet Explorer, cliquez sur **exécuter**.  
  
    > [!IMPORTANT]  
    >  Exécutez uniquement les fichiers provenant de sources fiables.  
  
5.  L'Assistant Générateur de rapports Microsoft SQL Server démarre.  
  
6.  Sur le **Bienvenue dans l’Assistant Installation** , cliquez sur **suivant**.  
  
7.  Sur le **contrat de licence** page, lisez le contrat, puis sélectionnez le **J’accepte les termes du contrat de licence** option. Cliquez sur **Suivant**.  
  
8.  Spécifiez votre nom et le nom de la société. Cliquez sur **Suivant**.  
  
9. Sur le **sélection des fonctionnalités** page, cliquez éventuellement sur **Parcourir** ou **disque coût**. Cliquez sur **Suivant**.  
  
    -   Cliquez sur **Parcourir** pour afficher l’emplacement par défaut du Générateur de rapports et de mettre à jour.  
  
        > [!NOTE]  
        >  Le dossier d’installation par défaut pour le Générateur de rapports est \<lecteur > Program Files\Microsoft SQL Server.  
  
    -   Cliquez sur **disque coût** pour en savoir plus la quantité d’espace disque le Générateur de rapports consomme.  
  
        > [!NOTE]  
        >  Si l'espace disque libre sur un volume n'est pas suffisant, le volume est mis en surbrillance.  
  
10. Dans la page **Serveur cible par défaut** , spécifiez éventuellement l'URL du serveur de rapports cible s'il est différent du serveur par défaut. Cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Si vous prévoyez de travailler avec le Générateur de rapports lorsqu'il est connecté à un serveur de rapports, il est plus commode de spécifier l'URL du serveur à ce stade. Toutefois, vous pouvez également le faire à partir de la **Options** boîte de dialogue lorsque vous travaillez dans le Générateur de rapports.  
  
11. Cliquez sur **installer** pour terminer l’installation du Générateur de rapports.  
  
### <a name="to-install-report-builder-from-a-share"></a>Pour installer le Générateur de rapports à partir d'un partage  
  
1.  Contactez votre administrateur afin de connaître l'emplacement du fichier ReportBuilder3_x86.msi que vous exécutez pour installer le Générateur de rapports sur votre ordinateur local.  
  
2.  Recherchez le fichier ReportBuilder3_x86.msi, le package MSI Windows Installer pour le Générateur de rapports, puis cliquez dessus.  
  
     L'Assistant Générateur de rapports Microsoft SQL Server démarre.  
  
3.  Sur le **Bienvenue dans l’Assistant Installation** , cliquez sur **suivant**.  
  
4.  Sur le **contrat de licence** page, lisez le contrat, puis sélectionnez le **J’accepte les termes du contrat de licence** option. Cliquez sur **Suivant**.  
  
5.  Spécifiez votre nom et le nom de la société. Cliquez sur **Suivant**.  
  
6.  Sur le **sélection des fonctionnalités** page, cliquez éventuellement sur **Parcourir** ou **disque coût**. Cliquez sur **Suivant**.  
  
    -   Cliquez sur **Parcourir** pour afficher l’emplacement par défaut du Générateur de rapports et de mettre à jour.  
  
        > [!NOTE]  
        >  Le dossier d’installation par défaut pour le Générateur de rapports est \<lecteur > Program Files\Microsoft SQL Server.  
  
    -   Cliquez sur **disque coût** pour en savoir plus la quantité d’espace disque le Générateur de rapports consomme.  
  
        > [!NOTE]  
        >  Si l'espace disque libre sur un volume n'est pas suffisant, le volume est mis en surbrillance.  
  
7.  Dans la page **Serveur cible par défaut** , spécifiez éventuellement l'URL du serveur de rapports cible s'il est différent du serveur par défaut. Cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Si vous prévoyez de travailler avec le Générateur de rapports lorsqu'il est connecté à un serveur de rapports, il est plus commode de spécifier l'URL du serveur à ce stade. Toutefois, vous pouvez également le faire à partir de la **Options** boîte de dialogue lorsque vous travaillez dans le Générateur de rapports.  
  
8.  Cliquez sur **installer** pour terminer l’installation du Générateur de rapports.  
  
### <a name="to-install-report-builder-from-the-command-line"></a>Pour installer le Générateur de rapports à partir de la ligne de commande  
  
1.  Accédez à [Générateur de rapports Microsoft SQL Server 2012](http://go.microsoft.com/fwlink/?LinkID=219138) et recherchez la section Générateur de rapports.  
  
2.  Cliquez sur **X86 Package**.  
  
3.  Cliquez sur Enregistrer.  
  
4.  Si vous le souhaitez, accédez à l’emplacement d’enregistrement pour vérifier la **enregistrer en tant que** option est **Package de programme d’installation de Windows**, puis cliquez sur **enregistrer**.  
  
5.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
6.  Dans la zone de texte Ouvrir, tapez `cmd.`  
  
7.  Dans la fenêtre d'invite de commandes, naviguez jusqu'au dossier où vous avez enregistré ReportBuilder3_x86.msi.  
  
8.  Tapez une commande au format suivant :  
  
     `msiexec/i ReportBuilder3_.msi /option [value] [/option [value]]`  
  
     Les deux options spécifiques à l'installation du Générateur de rapports sont : RBINSTALLDIR et REPORTSERVERURL. Il n'est pas obligatoire d'inclure ces arguments dans la ligne de commande. Voici la ligne de commande de base :  
  
     `msiexec /i ReportBuilder3_x86.msi /quiet`  
  
9. Pour exécuter la commande, appuyez sur Entrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer, désinstaller et prise en charge du Générateur de rapports](../install-uninstall-and-report-builder-support.md)   
 [Désinstaller la Version autonome du Générateur de rapports &#40;Générateur de rapports&#41;](install-report-builder.md)  
  
  
