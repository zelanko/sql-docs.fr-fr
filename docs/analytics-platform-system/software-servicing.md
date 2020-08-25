---
title: Maintenance logicielle
description: Maintenance des logiciels dans Analytics Platform System (APS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 4325dfa9c16edba12c2bba694b47c1b0875c7c6f
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "74400313"
---
# <a name="software-servicing-in-analytics-platform-system"></a>Maintenance des logiciels dans Analytics Platform System
Cette section résume les exigences de maintenance logicielle pour les appliances Analytics Platform System, y compris les correctifs logiciels WSUS et Analytics Platform System.  
  
## <a name="software-servicing-basics"></a><a name="Basics"></a>Notions de base de la maintenance des logiciels  
**WSUS :** Votre appliance Analytics Platform System doit être configurée pour recevoir des mises à jour de Windows Server Update Services (WSUS). Ces mises à jour incluent des modifications importantes apportées au logiciel de l’appliance. Une fois configurés, de nombreuses mises à jour sont installées automatiquement et ne nécessitent pas de gestion manuelle. En règle générale, les mises à jour WSUS sont configurées lors de la configuration de l' [Windows Server Update Services &#40;wsus&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md) effectuées pendant la configuration de l’appliance. Si ce n’est pas le cas, cette étape de configuration peut être effectuée ultérieurement. Pour plus d’informations sur WSUS, consultez le [Guide du site Web WSUS](https://go.microsoft.com/fwlink/?LinkId=202417).  
  
**Correctifs logiciels :** En outre, vous devrez peut-être appliquer des correctifs logiciels Analytics Platform System. Un *correctif* logiciel est une mise à jour logicielle créée pour un client spécifique afin de résoudre un problème lié au logiciel système de la plateforme d’analyse. Chaque correctif est un fichier exécutable qui installe le correctif pour le problème spécifique au client. Chaque correctif contient également une accumulation de toutes les mises à jour logicielles précédemment publiées pour Windows, SQL Server et Analytics Platform System. Si vous devez installer un correctif, le support technique Microsoft vous fournira le correctif et les instructions.  
  
**Étendue des mises à jour :** L’application d’un correctif logiciel ou d’un Service Pack au système Analytics Platform System doit mettre l’ensemble de l’appliance hors connexion.  
  
**Adaptateur de destination SSIS et outils clients :** Lors de l’application d’un correctif qui comprend les modifications apportées à la MSI de l’adaptateur de destination SSIS ou du fichier MSI des outils clients, les fichiers MSI sont mis à jour dans le répertoire **C:\PDWINST\ClientTools** du nœud de contrôle. Le correctif logiciel n’installe pas automatiquement les composants à partir des fichiers MSI mis à jour. Pour mettre à jour ces composants, le client doit désinstaller les anciennes versions des composants et installer les nouvelles versions à partir des fichiers MSI mis à jour. Lors de la désinstallation d’un correctif qui comprend les modifications apportées au MSI de l’adaptateur de destination SSIS ou à l’outil MSI des outils clients, les fichiers MSI de ces composants seront rétablis aux versions précédentes. Pour rétablir la version précédente de ces composants, le client doit désinstaller les versions existantes (plus récentes) des composants, puis réinstaller les versions antérieures à partir des fichiers MSI rétablis.  
  
## <a name="software-servicing-topics"></a>Rubriques relatives à la maintenance des logiciels  
Les rubriques suivantes décrivent comment gérer la maintenance des logiciels sur l’appliance :  
  
-   [Téléchargez et appliquez les mises à jour Microsoft &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)  
  
-   [Désinstallez les mises à jour Microsoft &#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
  
-   [Appliquer des correctifs logiciels Analytics Platform System &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
  
-   [Désinstallation des correctifs du système de plateforme Analytics &#40;Analytics&#41;](uninstall-analytics-platform-system-hotfixes.md)  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
