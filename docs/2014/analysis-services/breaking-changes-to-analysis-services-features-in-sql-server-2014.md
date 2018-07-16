---
title: Modifications avec rupture Analysis Services des fonctionnalités dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- breaking changes [Analysis Services]
- upgrading Analysis Services
ms.assetid: aeb02542-5a6c-458c-a110-13413dd3e9d9
caps.latest.revision: 46
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a00010f10148d4ed949a7d5602a68fb6a53b3f6e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238049"
---
# <a name="breaking-changes-to-analysis-services-features-in-sql-server-2014"></a>Modifications avec rupture dans les fonctionnalités Analysis Services de SQL Server 2014
  Cette rubrique décrit les changements importants apportés à [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)]. Ces modifications peuvent interrompre les applications, scripts ou fonctionnalités fondés sur les versions antérieures de SQL Server.  
  
 Dans cette rubrique :  
  
-   [Modifications avec rupture dans SQL Server 2014](#bkmk_sql2014)  
  
-   [Modifications avec rupture dans SQL Server 2012 SP1](#bkmk_2012Sp1)  
  
-   [Modifications avec rupture dans SQL Server 2012](#bkmk_sql11)  
  
-   [Modifications avec rupture dans SQL Server 2008/SQL Server 2008 R2](#bkmk_sql10)  
  
##  <a name="bkmk_sql2014"></a> Modifications avec rupture dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Il existe aucune nouvelle annoncées tabulaire, multidimensionnel, exploration de données, des modifications avec rupture ou [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] fonctionnalités dans cette version.  Toutefois, étant donné que [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] ressemble beaucoup à la [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] et [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] versions, les dernières modifications des deux versions précédentes sont fournies ici à titre informatif au cas où vous mettez à niveau à partir de [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].  
  
##  <a name="bkmk_2012Sp1"></a> Modifications avec rupture dans SQL Server 2012 SP1  
 Des modifications du code liées à la globalisation provoquent l'arrêt de certaines applications. Problèmes connus :  
  
 **Respect de la casse des identificateurs d’objets**  
 Une modification du code destinée à faire en sorte que tous les identificateurs d'objets ne respectent pas la casse a l'effet inverse pour certaines langues. L'objectif est que tous les identificateurs d'objets ne respectent pas la casse, quel que soit le classement. Ce changement aligne Analysis Services avec d'autres applications généralement utilisées dans la même pile de solution.  
  
 Pour les langues basées sur les 26 caractères de l'alphabet latin de base, les identificateurs d'objets ne respectent désormais plus la casse, ce qui correspond au comportement souhaité.  
  
 Pour le cyrillique et d'autres scripts de langues bicamérales qui utilisent la casse (grec, arménien et copte) les identificateurs d'objets respectent désormais la casse. Des modifications avec rupture sont susceptibles de se produire en cas de différence de casse entre un identificateur d'objet et la façon dont il est référencé (par exemple, un script de traitement qui fait référence à l'identificateur d'objet tout en minuscules). Ce comportement est susceptible de changer à l'avenir, mais comme solution de contournement temporaire, nous vous suggérons de modifier les scripts pour qu'ils utilisent la même casse que l'identificateur d'objet.  
  
##  <a name="bkmk_sql11"></a> Modifications avec rupture dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 Cette section documente les changements essentiels signalés pour les fonctionnalités d'[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
|Problème|Description|  
|-----------|-----------------|  
|Commandes du programme d'installation supprimées pour une installation de [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)].|Le programme d'installation installe mais ne configure plus [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)]. Les commandes du programme d'installation qui collectaient des valeurs utilisées pour les actions de configuration sont maintenant supprimées. Celles-ci comprennent notamment /FARMACCOUNT, /FARMPASSWORD, /PASSPHRASE et /FARMADMINPORT.<br /><br /> Si vous avez créé des scripts d'installation pour une installation sans assistance, vous devez modifier ces scripts pour une installation de [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)]. L'autre méthode consiste à utiliser des applets de commande PowerShell pour configurer le serveur en mode sans assistance. Pour plus d’informations, consultez [installation de PowerPivot à partir de l’invite de commandes](../../2014/sql-server/install/install-powerpivot-from-the-command-prompt.md) et [Configuration de PowerPivot à l’aide de Windows PowerShell](power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md).|  
  
##  <a name="bkmk_sql10"></a> Modifications avec rupture dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]/[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]  
 Cette section contient les modifications avec rupture des versions précédentes. Si vous effectuez une mise à niveau de [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], vous devez consulter les modifications avec rupture ajoutées dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] et [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)].  
  
|Problème|Description|  
|-----------|-----------------|  
|La fonction shallow exists fonctionne différemment maintenant avec les jeux nommés qui contiennent des membres énumérés ou des jointures croisées d'enumsets.|Dans [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)], la fonction shallow exists ne fonctionnait pas avec les jeux nommés qui contenant des membres énumérés ou des jointures croisées d'enumsets. Pour la compatibilité descendante avec l’original release version et SP1 de [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)], définissez la propriété de configuration « ConfigurationSettings\OLAP\Query\NamedSetShallowExistsMode », 1, ou pour la compatibilité descendante avec [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)] SP2, affectez-lui la valeur 2.|  
|Fonctions VBA ne gèrent les valeurs null et vides comme elles étaient gérées dans [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)]|Dans [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)], les fonctions de VBA retournaient la valeur 0 ou une chaîne vide lorsque des valeurs null ou vides étaient utilisées comme arguments. Dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], elles retournent la valeur NULL.|  
|L'Assistant Migration échouera parce que DSO n'est pas installé par défaut.|Par défaut, SQL Server 2008 n'installe pas le composant de compatibilité descendante DSO (Decision Support Objects). Le package de compatibilité descendante est installé par défaut mais le composant DSO du package sera désactivé. Dans la mesure où l'Assistant Migration SQL Server Analysis Services compte sur ce composant, il échouera à moins que le composant ne soit installé. Pour installer les composants DSO, procédez comme indiqué ci-dessous :<br /><br /> (1) Ouvrez le panneau de configuration.<br />(2) dans Windows XP ou Windows Server 2003, sélectionnez **Ajout / Suppression de programmes**. Dans Windows Vista et Windows Server 2008, sélectionnez **Programmes et fonctionnalités**.<br />(3) avec le bouton droit **compatibilité descendante de Microsoft SQL Server 2005**, puis sélectionnez **modification**.<br />(4) dans l’Assistant Installation de compatibilité descendante, cliquez sur **suivant**.<br />(5) dans la page Maintenance du programme, sélectionnez **modifier**, puis cliquez sur **suivant**.<br />(6) dans la page de sélection de fonctionnalités, si les objets DSO (Decision Support) n’est pas disponible, cliquez sur la flèche vers le bas et sélectionnez **ce composant sera installé sur le disque dur local**. Cliquez sur **Suivant**.<br />(7) sur la prêt à modifier la page du programme, cliquez sur **installer**.<br />(8) lorsque l’installation est terminée, cliquez sur **Terminer**.<br /><br /> <br /><br /> Vous pouvez supprimer DSO après la migration en suivant les étapes précédentes, en remplaçant l'option de DSO par**Ce composant ne sera pas disponible.**<br /><br /> Si le package de compatibilité descendante n'est pas installé, vous pouvez l'installer à partir du support de distribution de SQL Server 2008. Notez qu'il existe des versions pour chaque architecture cible (x86, x64, ia64). Ces versions se trouvent aux emplacements suivants :<br /><br /> x86\Setup\x86\SQLServer2005_BC.msi<br /><br /> x64\Setup\x64\SQLServer2005_BC .msi<br /><br /> ia64\Setup\ia64\SQLServer2005_BC.msi|  
|Il n'est pas recommandé de mettre l'emplacement de partition dans le dossier des données.|Le serveur gère le dossier des données et crée ou supprime des dossiers à mesure que les objets sont créés, supprimés et modifiés. Par conséquent, il est fortement déconseillé de spécifier un emplacement de stockage de partition à l'intérieur du dossier des données, surtout dans les sous-dossiers des bases de données, des cubes et des dimensions. Bien que le serveur vous permette d'effectuer cette action à l'aide de CREATE ou ALTER, il affiche un avertissement. Lorsque la mise à niveau de bases de données à partir de SQL Server 2005 Analysis Services à [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] Analysis Services qui ont des emplacements de stockage de partition dans le dossier de données, il fonctionnera. La restauration ou la synchronisation nécessitera le déplacement des emplacements de stockage de partition à l'extérieur du dossier Data.|  
|Vous pouvez obtenir des résultats inattendus pour les requêtes qui utilisent le mot clé MDX « EXISTING » dans ProClarity Analytics Server et Microsoft Office PerformancePoint Server 2007.|ProClarity Analytics Server et Microsoft Office PerformancePoint Server 2007 utilisent le mot clé EXISTING de MDX incorrectement dans certains scénarios. En raison de modifications apportées dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] Analysis Services, ces requêtes peuvent retourner des résultats inattendus.|  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité descendante d’Analysis Services](analysis-services-backward-compatibility.md)  
  
  
