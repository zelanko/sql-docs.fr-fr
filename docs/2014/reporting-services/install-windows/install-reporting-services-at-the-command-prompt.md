---
title: Installation d’invite de commandes de Reporting Services en Mode SharePoint et en Mode natif | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 048169b3-512c-41e4-895a-0416eff41268
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fc1e5ae5d17d45b937a5dd44ab3ea6fe5f8620eb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66108780"
---
# <a name="command-prompt-installation-of-reporting-services-sharepoint-mode-and-native-mode"></a>Installation d'invite de commandes en mode natif et en mode SharePoint de Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] prend en charge l’installation à partir de la ligne de commande du programme d’installation de SQL Server. Cette rubrique contient plusieurs exemples d'installations à partir de la ligne de commande spécifiques à [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Pour obtenir une description complète des options de ligne de commande disponibles pour tous les composants de SQL Server, consultez [installer SQL Server 2014 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md). Cette rubrique ne décrit pas les options de ligne de commande du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint. Pour plus d’informations sur l’installation du complément à partir de la ligne de commande, consultez [Installer le complément à l’aide du fichier d’installation rsSharePoint.msi](install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md#bkmk_install_rssharepoint).  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif  
  
## <a name="rsinstallmode-native-mode"></a>RSINSTALLMODE (mode natif)  
 Le paramètre d’entrée principal pour installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est le paramètre d’entrée **/RSINSTALLMODE** . Le paramètre présente deux options : **DefaultNativeMode** et **FilesOnlyMode**  
  
 Si le programme d'installation inclut le moteur de base de données SQL Server, la valeur par défaut RSINSTALLMODE est DefaultNativeMode. Si l'installation n'inclut pas le moteur de base de données SQL Server, la valeur par défaut RSINSTALLMODE est FilesOnlyMode. Si vous choisissez DefaultNativeMode mais que l'installation n'inclut pas le moteur de base de données SQL Server, le programme d'installation modifie automatiquement RSINSTALLMODE en FilesOnlyMode. Pour plus d’informations sur les paramètres d’entrée, consultez [installer SQL Server 2014 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
## <a name="rsshpinstallmode-sharepoint-mode"></a>RSSHPINSTALLMODE (mode SharePoint)  
 Le paramètre d’entrée pour installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint est **/RSSHPINSTALLMODE**. Le paramètre d’entrée a une option : SharePointFilesOnlyMode. L'option installe tous les fichiers nécessaires pour le mode SharePoint mais une configuration est requise après l'installation. Les étapes de configuration supplémentaires sont complétées à l'aide de l'Administration centrale de SharePoint. Pour en savoir plus, consultez la section [Installer le mode SharePoint de Reporting Services pour SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).  
  
## <a name="examples-of-sharepoint-mode-installation"></a>Exemples d'installation en mode SharePoint  
 L'exemple suivant installe SQL Server, le service moteur de base de données et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint ainsi que le complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour SharePoint (RS_SHPWFE).  
  
```  
setup /q /ACTION=install /FEATURES=SQL, RS_SHP, RS_SHPWFE,TOOLS /INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /SQLSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /AGTSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE"  
```  
  
 L'exemple suivant installe uniquement le mode SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
```  
Setup.exe /q /ACTION="Install" /IACCEPTSQLSERVERLICENSETERMS /FEATURES="RS_SHP" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SECURITYMODE="SQL" /SAPWD="*****" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Name]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="[Account Name]" /UPDATEENABLED="False"  
  
```  
  
 L'exemple suivant installe toutes les fonctionnalités de SQL Server, y compris le mode SharePoint et le mode natif [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT, RS_SHP,RS_SHPWFE,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSSHPINSTALLMODE="SharePointFilesOnlyMode" /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="examples-of-sharepoint-mode-upgrade"></a>Exemples de mise à niveau en mode SharePoint  
 L'exemple suivant met à niveau le mode SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . **RSUPGRADEPASSWORD** est le mot de passe du compte de service Report Server existant. RSUPGRADEPASSWORD est un champ obligatoire dans un scénario de mise à niveau, à moins que le compte de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne soit un compte intégré.  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[PID value]" /FTSVCACCOUNT="[DOMAIN\ACCOUNT]" /FTSVCPASSWORD="[ACCOUNTPASSSWORD]" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSUPGRADEPASSWORD="******"  
```  
  
 L'exemple suivant peut être utilisé pour mettre à niveau une installation en mode SharePoint basée sur l'architecture de service partagé SharePoint. L'exemple suivant utilise le commutateur ALLOWUPGRADEFORSSRSSHAREPOINTMODE. Le commutateur n'est pas nécessaire pour mettre à niveau des versions antérieures qui ne sont pas basées sur l'architecture de service partagé :  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
```  
Setup.exe /q /ACTION="Upgrade" /INSTANCENAME="MSSQLSERVER" /PID="[Your PID Value]" /FTSVCACCOUNT="[ACCOUNT Name]" /FTSVCPASSWORD="****" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /ALLOWUPGRADEFORSSRSSHAREPOINTMODE="True"  
```  
  
## <a name="examples-of-native-mode-installation"></a>Exemples d'installation en mode natif  
  
```  
Setup.exe /q /ACTION="Install" /INSTANCENAME="MSSQLSERVER" /FEATURES="SQLEngine,Replication,SNAC,SNAC_SDK,Browser,Writer,AS,IS,MDS,Adv_SSMS,BC,BOL,Conn,SDK,DReplay_CTLR,DReplay_CLT,DQC,BIDS,FullText, RS,DQ,SSMS" /INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDDIR="C:\Program Files\Microsoft SQL Server" /INSTALLSHAREDWOWDIR="C:\Program Files (x86)\Microsoft SQL Server" /INSTALLSQLDATADIR="C:\Program Files\Microsoft SQL Server" /SQLSVCACCOUNT="[Account Name]" /SQLSVCPASSWORD="********" /AGTSVCACCOUNT="[Account Nam]" /AGTSVCPASSWORD="********" /CTLRSVCACCOUNT="[Account Nam]" /CTLRSVCPASSWORD="********" /CLTSVCACCOUNT="[Account Nam]" /CLTSVCPASSWORD="********" /ASSVCACCOUNT="[Account Nam]" /ASSVCPASSWORD="********" /RSSVCACCOUNT="[Account Nam]" /RSSVCPASSWORD="********" /FTSVCACCOUNT="[Account Nam]" /FTSVCPASSWORD="********" /SECURITYMODE="SQL" /SAPWD="********" /PID="[Your PID Value]" /SQLSYSADMINACCOUNTS="[Account Nam]" "AutoSql Admin Group" /ASSYSADMINACCOUNTS="BUILTIN\ADMINISTRATORS" /UPDATEENABLED="False" /IACCEPTSQLSERVERLICENSETERMS /RSINSTALLMODE="DefaultNativeMode"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Installer SQL Server 2014 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
 [Paramètres SysPrep](../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md#SysPrep)   
 [Installer PowerPivot à partir de l’invite de commandes](../../sql-server/install/install-powerpivot-from-the-command-prompt.md)  
  
  
