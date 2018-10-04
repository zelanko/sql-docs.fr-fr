---
title: Démarrer le Générateur de rapports (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Builder, launching
- launching Report Builder
- SharePoint integration [Reporting Services], starting Report Builder
- starting Report Builder
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 30fef45662f5cfa81e88ce740e556cdc0e66cf39
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48192499"
---
# <a name="start-report-builder-report-builder"></a>Démarrer le Générateur de rapports (Générateur de rapports)
  [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] comprend une version autonome et [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] versions du Générateur de rapports. La version [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] peut être utilisée avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif ou en mode intégré SharePoint.  
  
> [!NOTE]  
>  Il n'est pas possible d'installer le Générateur de rapports sur les ordinateurs Itanium 64. Cela s’applique à la [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] et des versions autonomes du Générateur de rapports.  
  
 Si la version [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] du Générateur de rapports qui s'ouvre est une version antérieure, contactez votre administrateur qui peut mettre à jour le Gestionnaire de rapports et le site SharePoint de façon à utiliser la version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] du Générateur de rapports  
  
 Vous pouvez également utiliser la version [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] du Générateur de rapports pour créer des rapports sur un classeur [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] publié sur SharePoint. Pour plus d’informations sur l’utilisation du Générateur de rapports avec [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], consultez [créer un rapport Reporting Services avec des données PowerPivot](http://go.microsoft.com/fwlink/?LinkId=185238) sur le site technet.microsoft.com.  
  
 Pour démarrer le Générateur de rapports autonome à partir de la **Démarrer** menu sur votre ordinateur local, vous ou un administrateur doit installer le Générateur de rapports directement sur votre ordinateur avant de l’outil est disponible que vous pouvez utiliser. La version autonome ne s'installe pas lorsque vous installez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ; vous devez la télécharger et l'installer séparément. Pour télécharger le Générateur de rapports, consultez [le Générateur de rapports Microsoft® SQL Server® 2012](http://go.microsoft.com/fwlink/?LinkId=401502).  
  
### <a name="to-start-report-builder-clickonce-from-report-manager"></a>Pour démarrer la version ClickOnce du Générateur de rapports à partir du Gestionnaire de rapports  
  
1.  Dans le navigateur Web, tapez l'URL du serveur de rapports dans la barre d'adresses. Par défaut, l’URL est http://\<*nom_serveur*>/reports. Le Gestionnaire de rapports s'ouvre.  
  
2.  Cliquez sur **Générateur de rapports**.  
  
     Le Générateur de rapports s'ouvre et vous pouvez alors créer un rapport ou ouvrir un rapport sur le serveur de rapports.  
  
### <a name="to-start-report-builder-clickonce-using-a-url"></a>Pour démarrer la version ClickOnce du Générateur de rapports à l'aide d'une URL  
  
1.  Dans le navigateur Web, tapez l'URL suivante dans la barre d'adresses :  
  
     http://\<nom_serveur > /reportserver/reportbuilder/ReportBuilder_3_0_0_0.application  
  
2.  Appuyez sur Entrée.  
  
     Le Générateur de rapports s'ouvre et vous pouvez alors créer un rapport ou ouvrir un rapport sur le serveur de rapports.  
  
### <a name="to-start-report-builder-clickonce-in-sharepoint-integrated-mode"></a>Pour démarrer la version ClickOnce du Générateur de rapports en mode intégré SharePoint  
  
1.  Naviguez jusqu'au site SharePoint qui contient la bibliothèque souhaitée.  
  
2.  Ouvrez la bibliothèque.  
  
3.  Cliquez sur **Documents**.  
  
4.  Dans le menu **Nouveau document** , cliquez sur **Rapport du Générateur de rapports**.  
  
     Le Générateur de rapports s'ouvre et vous pouvez alors créer un rapport ou ouvrir un rapport sur le serveur de rapports.  
  
     **Remarque** si le **Nouveau Document** menu ne répertorie pas les **rapport du Générateur de rapports**, **modèle du Générateur de rapports**, et **Source de données de rapport** options, leurs types de contenus doivent être ajoutés à la bibliothèque SharePoint. Pour plus d’informations, consultez [ajouter Types serveur de rapports contenus dans une bibliothèque &#40;Reporting Services en Mode intégré SharePoint&#41; ](../add-reporting-services-content-types-to-a-sharepoint-library.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [la documentation en ligne](http://go.microsoft.com/fwlink/?LinkId=154888) sur MSDN.Microsoft.com.  
  
### <a name="to-start-report-builder-stand-alone-from-the-start-menu"></a>Pour démarrer la version autonome du Générateur de rapports à partir du menu Démarrer  
  
1.  Dans le menu Démarrer, cliquez sur **tous les programmes**, puis cliquez sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)] **le Générateur de rapports**.  
  
2.  Cliquez sur **Générateur de rapports** .  
  
     Le Générateur de rapports s'ouvre et vous pouvez créer ou ouvrir un rapport.  
  
3.  Pour créer un rapport, cliquez sur l'icône SQL Server dans l'angle supérieur gauche du Générateur de rapports, puis cliquez sur Nouveau.  
  
4.  Pour ouvrir un rapport existant stocké sur votre ordinateur local ou sur un serveur de rapports, cliquez sur l'icône SQL Server dans l'angle supérieur gauche, puis cliquez sur Ouvrir.  
  
     Si vous ne voyez pas le serveur de rapports dans la liste des serveurs existants, fermez le **ouvrir le rapport** boîte de dialogue, puis cliquez sur **Connect** en bas du Générateur de rapports pour se connecter au serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Générateur de rapports dans SQL Server 2014](report-builder-in-sql-server-2016.md)  
  
  
