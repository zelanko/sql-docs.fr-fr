---
title: Désinstaller la Version autonome du Générateur de rapports (Générateur de rapports) | Documents Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 009538c6-4941-4393-b14b-9144cffdbdaf
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 5482ca3ec570b4155712dbeaf3768a55372eccad
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039009"
---
# <a name="uninstall-the-stand-alone-version-of-report-builder-report-builder"></a>Désinstaller la version autonome du Générateur de rapports (Générateur de rapports)
  Vous pouvez désinstaller la version autonome du Générateur de rapports à partir du Panneau de configuration ou de la ligne de commande. Vous ne pouvez pas désinstaller la version [!INCLUDE[ndptecclick](../../includes/ndptecclick-md.md)] du Générateur de rapports sans désinstaller [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)].  
  
 La désinstallation du Générateur de rapports à partir de la ligne de commande utilise une syntaxe identique à celle que vous utilisez pour installer le Générateur de rapports, à la différence près que vous utilisez l'option /x à la place de l'option /i. Les lignes de commande de désinstallation peuvent également inclure l'option /quiet et d'autres options standard. Si le package Windows Installer du Générateur de rapports (ReportBuilder3_x86.msi) a été supprimé, la ligne de commande ne permet pas de désinstaller facilement le Générateur de rapports. Pour en savoir plus sur la suppression du Générateur de rapports à l'aide de son GUID, consultez la documentation du programme msiexec dans MSDN Library.  
  
 Si les dossiers utilisés par le Générateur de rapports incluent des fichiers personnalisés, les dossiers et fichiers sont conservés lors de la suppression du Générateur de rapports. Seuls les fichiers du Générateur de rapports sont supprimés.  
  
### <a name="to-uninstall-report-builder-from-the-control-panel"></a>Pour désinstaller le Générateur de rapports à partir du panneau de configuration  
  
1.  Dans le menu **Démarrer** , cliquez sur **Panneau de configuration**.  
  
2.  Dans le Panneau de configuration, cliquez sur **Programmes et fonctionnalités**.  
  
3.  Recherchez Générateur de rapports [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dans la liste **Nom** , puis cliquez dessus.  
  
4.  Cliquez sur **Désinstaller**.  
  
5.  Si vous êtes invité à confirmer la désinstallation du Générateur de rapports, cliquez sur **Oui**.  
  
### <a name="to-uninstall-report-builder-from-the-command-line"></a>Pour désinstaller le Générateur de rapports à partir de la ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **ouvrir** zone de texte, tapez `cmd.`  
  
3.  Dans la fenêtre d'invite de commandes, naviguez jusqu'au dossier avec ReportBuilder3_x86.msi.  
  
4.  Tapez une ligne de commande de base, par exemple :  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v install.log`  
  
 Pour inclure l'enregistrement, utilisez une ligne de commande telle que :  
  
 `msiexec /x ReportBuilder3_x86.msi /quiet /l*v c:\junk\install.log`  
  
1.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer, désinstaller et prise en charge du Générateur de rapports](../install-uninstall-and-report-builder-support.md)   
 [Installer la Version autonome du Générateur de rapports &#40;Générateur de rapports&#41;](install-report-builder.md)  
  
  