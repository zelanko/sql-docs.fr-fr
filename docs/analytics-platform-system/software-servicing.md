---
title: Maintenance de logiciels - Analytique Platform System | Microsoft Docs
description: Analytique Platform System (APS) de maintenance logicielle.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 444d7f29e7f65da7e5d98dde310b2c1f8ad8dd4b
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51700208"
---
# <a name="software-servicing-in-analytics-platform-system"></a>Maintenance des logiciels d’Analytique Platform System
Cette section résume les logiciels de maintenance configuration requise pour les appliances Analytique Platform System, y compris les correctifs logiciels WSUS et Analytique Platform System.  
  
## <a name="Basics"></a>Bases de la maintenance des logiciels  
**WSUS :** votre appliance Analytique Platform System doit être configuré pour recevoir des mises à jour à partir de Windows Server Update Services (WSUS). Ces mises à jour incluent des modifications importantes apportées au logiciel de l’application. Une fois configurés, nombreuses mises à jour seront installera automatiquement et ne nécessitent pas de gestion pratique. En règle générale, les mises à jour WSUS sont configurés au cours de la [configurer Windows Server Update Services &#40;WSUS&#41; &#40;Analytique Platform System&#41; ](configure-windows-server-update-services-wsus.md) étape effectuée pendant la configuration de l’appliance. Si ce n’est pas le cas, cette étape de configuration peut être effectuée plus tard. Pour plus d’informations sur WSUS, consultez le [site Web WSUS Guide](https://go.microsoft.com/fwlink/?LinkId=202417).  
  
**Correctifs logiciels :** en outre, vous devrez peut-être appliquer des correctifs de système de plateforme d’Analytique. Un *correctif* est une mise à jour logicielle qui est créé pour un client spécifique résoudre un problème avec le logiciel de système de plateforme d’Analytique. Chaque correctif est un fichier exécutable qui installe le correctif pour le problème spécifique au client. Chaque correctif contient également une accumulation de toutes les mises à jour logicielles précédemment publiées pour Windows, SQL Server et Analytique Platform System. Si vous avez besoin d’installer un correctif logiciel, le support Microsoft vous fournira le correctif logiciel et les instructions.  
  
**Étendue des mises à jour :** appliquer un correctif logiciel ou service pack pour le système de plateforme Analytique doit mettre l’appliance entier hors connexion.  
  
**Adaptateur de Destination SSIS et outils clients :** lorsque vous appliquez un correctif logiciel qui inclut des modifications du MSI de l’adaptateur de Destination SSIS ou MSI du Client des outils, les fichiers MSI seront actualisées dans le **C:\PDWINST\ClientTools** répertoire sur le nœud de contrôle. Le correctif logiciel n’installe pas automatiquement les composants à partir des fichiers MSI mis à jour. Pour mettre à jour de ces composants, le client doit désinstaller les anciennes versions des composants et installer les nouvelles versions à partir des fichiers MSI mis à jour. Lors de la désinstallation d’un correctif logiciel qui inclut des modifications du MSI de l’adaptateur de Destination SSIS ou MSI du Client des outils, les fichiers MSI pour ces composants sera défini sur les versions précédentes. Pour annuler ces composants à une version antérieure, le client doit désinstaller les versions existantes (le plus récent) des composants et réinstaller les versions plus anciennes à partir des fichiers MSI rétablies.  
  
## <a name="software-servicing-topics"></a>Rubriques de la maintenance des logiciels  
Les rubriques suivantes décrivent comment gérer la maintenance des logiciels sur l’appliance :  
  
-   [Téléchargez et appliquez les mises à jour Microsoft &#40;Analytique Platform System&#41;](download-and-apply-microsoft-updates.md)  
  
-   [Désinstaller les mises à jour Microsoft &#40;Analytique Platform System&#41;](uninstall-microsoft-updates.md)  
  
-   [Appliquer des correctifs de système de plateforme Analytique &#40;Analytique Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
  
-   [Désinstallation de correctifs de système de plateforme Analytique &#40;Analytique Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
