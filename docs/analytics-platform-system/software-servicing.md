---
title: Logiciels (système de plateforme Analytique) de maintenance
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cec4d924-c88f-470c-84bb-0af3e21aabf1
caps.latest.revision: 33
ms.openlocfilehash: 8bddf00569ad4c5e5c78e801399b589a9f6d5f42
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="software-servicing"></a>Maintenance de logiciel
Cette section résume le logiciel de configuration requise pour les équipements de système de plateforme Analytique, y compris les correctifs logiciels WSUS et le système de plateforme d’Analytique de maintenance.  
  
## <a name="Basics"></a>Principes fondamentaux de la maintenance de logiciel  
**WSUS :** votre appliance Analytique plate-forme système doit être configuré pour recevoir des mises à jour à partir de Windows Server Update Services (WSUS). Ces mises à jour incluent des modifications importantes apportées au logiciel de l’application. Une fois qu’ils sont configurés, nombreuses mises à jour seront installe automatiquement et ne nécessitent pas de gestion pratique. En règle générale, les mises à jour WSUS sont configurés au cours de la [configurer Windows Server Update Services &#40;WSUS&#41; &#40;système de plateforme Analytique&#41; ](configure-windows-server-update-services-wsus.md) étape effectuée pendant la configuration de l’appliance. Si ce n’est pas le cas, cette étape de configuration peut être effectuée ultérieurement. Pour plus d’informations sur WSUS, consultez le [du site Web WSUS Guide](http://go.microsoft.com/fwlink/?LinkId=202417).  
  
**Les correctifs logiciels :** en outre, vous devrez peut-être appliquer des correctifs de système de plateforme Analytique. A *correctif* est une mise à jour logicielle qui est créé pour un client spécifique résoudre un problème avec le logiciel de système de plateforme Analytique. Chaque correctif logiciel est un fichier exécutable qui installe le correctif pour le problème spécifique au client. Chaque correctif contient également une accumulation de toutes les mises à jour logicielles précédemment publiées pour Windows, SQL Server et système de plateforme d’Analytique. Si vous avez besoin d’installer un correctif logiciel, prise en charge de Microsoft vous fournira les correctifs logiciels et les instructions.  
  
**Étendue des mises à jour :** appliquer un correctif logiciel ou service pack pour le système de plateforme Analytique doit déconnecter l’application entière. Autrement dit, le PDW et HDInsight régions seront affectées.  
  
**Adaptateur de Destination SSIS et outils clients :** lors de l’application d’un correctif logiciel qui inclut des modifications de MSI de l’adaptateur de Destination SSIS ou MSI du Client des outils, les fichiers MSI seront mise à jour dans le **C:\PDWINST\ClientTools** répertoire sur le nœud du contrôle. Le correctif logiciel n’installe pas automatiquement les composants à partir des fichiers MSI mis à jour. Pour mettre à jour ces composants, le client doit désinstaller les anciennes versions des composants et installer les nouvelles versions des fichiers MSI mis à jour. Lors de la désinstallation d’un correctif logiciel qui inclut des modifications de MSI de l’adaptateur de Destination SSIS ou MSI du Client des outils, les fichiers MSI pour ces composants vont être annulée pour les versions précédentes. Pour rétablir les composants à une version antérieure, le client doit désinstaller les versions existantes (plus récentes) des composants et réinstaller les anciennes versions des fichiers MSI restaurées.  
  
## <a name="software-servicing-topics"></a>Rubriques de la maintenance de logiciel  
Les rubriques suivantes décrivent comment gérer des logiciels de maintenance du matériel :  
  
-   [Téléchargez et appliquez les mises à jour Microsoft &#40;Analytique plate-forme système&#41;](download-and-apply-microsoft-updates.md)  
  
-   [Désinstaller les mises à jour Microsoft &#40;Analytique plate-forme système&#41;](uninstall-microsoft-updates.md)  
  
-   [Appliquer des correctifs de système de plateforme Analytique &#40;Analytique plate-forme système&#41;](apply-analytics-platform-system-hotfixes.md)  
  
-   [Désinstallation de correctifs de système de plateforme Analytique &#40;Analytique plate-forme système&#41;](uninstall-analytics-platform-system-hotfixes.md)  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
