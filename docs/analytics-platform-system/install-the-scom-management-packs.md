---
title: Installer les packs d’administration SCOM - Analytique Platform System | Microsoft Docs
description: Suivez ces étapes pour télécharger et installer les packs d’administration de System Center Operations Manager (SCOM) pour SQL Server PDW. Les packs d’administration sont requises pour analyser SQL Server PDW à partir de SCOM.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ac213e71d3754ccf610ba5c0874cea32c3737760
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960818"
---
# <a name="install-sql-server-operations-manager-scom-management-packs-for-analytics-platform-system"></a>Installer des packs d’administration de SQL Server Operations Manager (SCOM) pour le système de plateforme d’Analytique
Suivez ces étapes pour télécharger et installer les packs d’administration de System Center Operations Manager (SCOM) pour SQL Server PDW. Les packs d’administration sont requises pour analyser SQL Server PDW à partir de SCOM.  
  
## <a name="BeforeBegin"></a>Avant de commencer  
**Conditions préalables**  
  
System Center Operations Manager doit être installé et en cours d’exécution. SQL Server 2012 PDW nécessite System Center Operations Manager 2007 R2, System Center Operations Manager 2012 ou System Center Operations Manager 2012 service pack 1.  
  
## <a name="Step1"></a>Étape 1 : Télécharger les packs d’administration  
Pour la charge de travail APS PDW, téléchargez le [System Center Management Pack pour le système de plateforme d’Analytique Microsoft](https://go.microsoft.com/fwlink/?LinkId=396857).  
  
Pour la gestion de l’appliance, téléchargez le [le Pack d’administration de la Base de Appliance SQL Server](https://www.microsoft.com/download/details.aspx?displaylang=en&id=11436).  
  
Pour les versions antérieures de PDW sans APS, téléchargez le[Pack d’analyse System Center pour Microsoft SQL Server 2012 Parallel Data Warehouse Appliance](https://go.microsoft.com/fwlink/p/?LinkId=282661).  
  
<!-- MISSING LINKS - For the HDInsight workload, download the [System Center Management Pack for HDInsight](https://go.microsoft.com/fwlink/?LinkId=390208).  -->
  
## <a name="Step2"></a>Étape 2 : Installer les packs d’administration  
  
### <a name="install-the-sql-server-appliance-base-management-pack"></a>Installez le Pack de gestion de la Base de SQL Server Appliance  
  
1.  Pour exécuter l’installation, double-cliquez sur le Pack d’administration Base téléchargé SQL Server Appliance.  
  
2.  Acceptez le contrat de licence, puis cliquez sur **suivant**.  
  
    ![Acceptez le contrat de licence](./media/install-the-scom-management-packs/SCOM_licnse_agrmt.png "SCOM_licnse_agrmt")  
  
3.  Sélectionner votre propre dossier d’installation, ou utiliser la valeur par défaut du dossier d’Installation de Pack de gestion.  
  
    ![Sélectionnez le dossier d’Installation](./media/install-the-scom-management-packs/SCOM_licnse_agrmt2.png "SCOM_licnse_agrmt2")  
  
4.  Cliquez sur **Installer**.  
  
    ![Confirmer l’installation](./media/install-the-scom-management-packs/SCOM_licnse_agrmt3.png "SCOM_licnse_agrmt3")  
  
5.  Cliquez sur **Fermer**.  
  
    ![Cliquez sur Fermer](./media/install-the-scom-management-packs/SCOM_licnse_agrmt4.png "SCOM_licnse_agrmt4")  
  
### <a name="install-the-monitoring-pack-for-sql-server-pdw-appliance"></a>Installer le Pack de surveillance pour SQL Server PDW Appliance  
  
1.  Pour exécuter l’installation, double-cliquez sur le Pack d’administration Appliance téléchargé SQL Server PDW.  
  
2.  Acceptez le contrat de licence, puis cliquez sur **suivant**.  
  
    ![Acceptez le contrat de licence](./media/install-the-scom-management-packs/SCOM_licnse_agmtB.png "SCOM_licnse_agmtB")  
  
3.  Choisissez le répertoire qui contiendra les fichiers extraits. Le dossier d’installation de Pack d’administration par défaut s’affichent par défaut. Sélectionnez la valeur par défaut, ou votre propre dossier d’installation.  
  
    ![Dossier d’installation sélectionnez](./media/install-the-scom-management-packs/SCOM_licnse_agmtB1.png "SCOM_licnse_agmtB1")  
  
4.  Cliquez sur **Installer**.  
  
    ![Confirmer l’installation](./media/install-the-scom-management-packs/SCOM_licnse_agmtB2.png "SCOM_licnse_agmtB2")  
  
5.  Cliquez sur **Fermer**.  
  
    ![Installation terminée](./media/install-the-scom-management-packs/SCOM_licnse_agmtB3.png "SCOM_licnse_agmtB3")  
  
## <a name="next-step"></a>Étape suivante  
Maintenant que vous avez les packs d’administration installés, passez à l’étape suivante : [Importer le Pack d’administration SCOM pour PDW &#40;Analytique Platform System&#41;](import-the-scom-management-pack-for-pdw.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
