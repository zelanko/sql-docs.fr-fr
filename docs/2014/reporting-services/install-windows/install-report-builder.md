---
title: Installer la version autonome de Générateur de rapports (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6b2291bb-1d20-4d08-81cb-a16dd8e01faf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 60a96db6a7568c2af22242f10f96e7a2abf13937
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73637837"
---
# <a name="install-the-stand-alone-version-of-report-builder-report-builder"></a>Installer la version autonome du Générateur de rapports (Générateur de rapports)
  Vous pouvez installer Générateur de rapports à partir [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du Feature Pack dans le [Centre de téléchargement Microsoft](https://www.microsoft.com/download/details.aspx?id=53613) ou à un emplacement tel que le dossier public dans lequel le ReportBuilder3_x86. msi, le package Windows Installer pour générateur de rapports, a été téléchargé.  
  
 Vous pouvez également effectuer une installation du Générateur de rapports à partir de la ligne de commande et spécifier des arguments afin de personnaliser l'installation. Outre les paramètres MSI standard intrinsèques, vous pouvez utiliser les paramètres personnalisés fournis par le Générateur de rapports : RBINSTALLDIR et REPORTSERVERURL. RBINSTALLDIR spécifie le dossier d'installation racine pour le Générateur de rapports. REPORTSERVERURL spécifie le serveur de rapports par défaut utilisé par le Générateur de rapports pour enregistrer des rapports.  
  
 Si vous souhaitez effectuer une installation totalement sans assistance, sans aucune interaction avec l’interface utilisateur, spécifiez l’option **/quiet** . Par défaut, l'indicateur d'option quiet supprime les erreurs d'installation. Il est par conséquent recommandé d’inclure l’option **/l** , qui spécifie l’enregistrement dans le journal, lorsque vous utilisez l’option quiet.  
  
> [!IMPORTANT]  
>  Les fonctionnalités de sécurité de Windows Vista et Windows 7 requièrent des autorisations élevées pour exécuter des opérations en ligne de commande ; par conséquent, vous êtes invité à confirmer que vous avez l'autorisation d'exécuter la ligne de commande. Il ne s'agit pas d'une installation sans assistance. Pour effectuer une installation sans assistance, vous devez exécuter la ligne de commande en tant qu'administrateur.  
  
### <a name="to-install-report-builder-from-the-download-site"></a>Pour installer le Générateur de rapports à partir du site de téléchargement  
  
1.  Accédez à [Microsoft SQL Server 2012 générateur de rapports](https://go.microsoft.com/fwlink/?LinkID=219138) et recherchez la section générateur de rapports de la page Web.  
  
2.  Cliquez sur **package x86**.  
  
3.  Dans la boîte de dialogue **téléchargement de fichier** , cliquez sur **exécuter**.  
  
    > [!IMPORTANT]  
    >  Téléchargez uniquement les fichiers provenant de sources fiables.  
  
4.  Dans la boîte de dialogue Internet Explorer, cliquez sur **exécuter**.  
  
    > [!IMPORTANT]  
    >  Exécutez uniquement les fichiers provenant de sources fiables.  
  
5.  L'Assistant Générateur de rapports Microsoft SQL Server démarre.  
  
6.  Sur la page **Bienvenue dans l’Assistant Installation** , cliquez sur **suivant**.  
  
7.  Sur la page **contrat de licence** , lisez le contrat, puis sélectionnez l’option **J’accepte les termes du contrat de licence** . Cliquez sur **Suivant**.  
  
8.  Spécifiez votre nom et le nom de la société. Cliquez sur **Suivant**.  
  
9. Sur la page **sélection de composant** , cliquez éventuellement sur **Parcourir** ou coût du **disque**. Cliquez sur **Suivant**.  
  
    -   Cliquez sur **Parcourir** pour afficher l’emplacement par défaut de générateur de rapports et le mettre à jour.  
  
        > [!NOTE]  
        >  Le dossier d’installation par défaut de \<générateur de rapports est lecteur>Program Files\Microsoft SQL Server.  
  
    -   Cliquez sur **coût du disque** pour connaître la quantité d’espace disque consommée par générateur de rapports.  
  
        > [!NOTE]  
        >  Si l'espace disque libre sur un volume n'est pas suffisant, le volume est mis en surbrillance.  
  
10. Dans la page **Serveur cible par défaut** , spécifiez éventuellement l'URL du serveur de rapports cible s'il est différent du serveur par défaut. Cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Si vous prévoyez de travailler avec le Générateur de rapports lorsqu'il est connecté à un serveur de rapports, il est plus commode de spécifier l'URL du serveur à ce stade. Toutefois, vous pouvez également effectuer cette opération à partir de la boîte de dialogue **options** lorsque vous travaillez dans générateur de rapports.  
  
11. Cliquez sur **installer** pour terminer l’installation de générateur de rapports.  
  
### <a name="to-install-report-builder-from-a-share"></a>Pour installer le Générateur de rapports à partir d'un partage  
  
1.  Contactez votre administrateur afin de connaître l'emplacement du fichier ReportBuilder3_x86.msi que vous exécutez pour installer le Générateur de rapports sur votre ordinateur local.  
  
2.  Recherchez le fichier ReportBuilder3_x86.msi, le package MSI Windows Installer pour le Générateur de rapports, puis cliquez dessus.  
  
     L'Assistant Générateur de rapports Microsoft SQL Server démarre.  
  
3.  Sur la page **Bienvenue dans l’Assistant Installation** , cliquez sur **suivant**.  
  
4.  Sur la page **contrat de licence** , lisez le contrat, puis sélectionnez l’option **J’accepte les termes du contrat de licence** . Cliquez sur **Suivant**.  
  
5.  Spécifiez votre nom et le nom de la société. Cliquez sur **Suivant**.  
  
6.  Sur la page **sélection de composant** , cliquez éventuellement sur **Parcourir** ou coût du **disque**. Cliquez sur **Suivant**.  
  
    -   Cliquez sur **Parcourir** pour afficher l’emplacement par défaut de générateur de rapports et le mettre à jour.  
  
        > [!NOTE]  
        >  Le dossier d’installation par défaut de \<générateur de rapports est lecteur>Program Files\Microsoft SQL Server.  
  
    -   Cliquez sur **coût du disque** pour connaître la quantité d’espace disque consommée par générateur de rapports.  
  
        > [!NOTE]  
        >  Si l'espace disque libre sur un volume n'est pas suffisant, le volume est mis en surbrillance.  
  
7.  Dans la page **Serveur cible par défaut** , spécifiez éventuellement l'URL du serveur de rapports cible s'il est différent du serveur par défaut. Cliquez sur **Suivant**.  
  
    > [!NOTE]  
    >  Si vous prévoyez de travailler avec le Générateur de rapports lorsqu'il est connecté à un serveur de rapports, il est plus commode de spécifier l'URL du serveur à ce stade. Toutefois, vous pouvez également effectuer cette opération à partir de la boîte de dialogue **options** lorsque vous travaillez dans générateur de rapports.  
  
8.  Cliquez sur **installer** pour terminer l’installation de générateur de rapports.  
  
### <a name="to-install-report-builder-from-the-command-line"></a>Pour installer le Générateur de rapports à partir de la ligne de commande  
  
1.  Accédez à [Microsoft SQL Server 2012 générateur de rapports](https://go.microsoft.com/fwlink/?LinkID=219138) et recherchez la section générateur de rapports.  
  
2.  Cliquez sur **package x86**.  
  
3.  Cliquez sur Enregistrer.  
  
4.  Si vous le souhaitez, accédez à l’emplacement où vous souhaitez enregistrer, vérifiez que l’option **Enregistrer sous** est **Windows Installer Package**, puis cliquez sur **Enregistrer**.  
  
5.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
6.  Dans la zone de texte Ouvrir, tapez .`cmd.`  
  
7.  Dans la fenêtre d'invite de commandes, naviguez jusqu'au dossier où vous avez enregistré ReportBuilder3_x86.msi.  
  
8.  Tapez une commande au format suivant :  
  
     `msiexec/i ReportBuilder3_.msi /option [value] [/option [value]]`  
  
     Les deux options spécifiques à l'installation du Générateur de rapports sont : RBINSTALLDIR et REPORTSERVERURL. Il n'est pas obligatoire d'inclure ces arguments dans la ligne de commande. Voici la ligne de commande de base :  
  
     `msiexec /i ReportBuilder3_x86.msi /quiet`  
  
9. Pour exécuter la commande, appuyez sur Entrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer, désinstaller et Générateur de rapports la prise en charge](../install-uninstall-and-report-builder-support.md)   
 [Désinstallez la version autonome de Générateur de rapports &#40;Générateur de rapports&#41;](install-report-builder.md)  
  
  
