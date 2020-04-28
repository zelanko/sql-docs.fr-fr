---
title: Importer le pack d’administration SCOM
description: Procédez comme suit pour importer les packs d’administration System Center Operations Manager (SCOM) pour Analytics Platform System (APS). Les packs d’administration sont requis pour analyser les Data Warehouse parallèles à partir de SCOM.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: bcb0e667424767fd53a5fc7e027e84d512022203
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401082"
---
# <a name="import-the-scom-management-pack---analytics-platform-system"></a>Importer le pack d’administration SCOM-Analytics Platform System
Procédez comme suit pour importer les packs d’administration System Center Operations Manager (SCOM) pour Analytics Platform System (APS). Les packs d’administration sont requis pour analyser les Data Warehouse parallèles à partir de SCOM. 
  
## <a name="before-you-begin"></a><a name="BeforeBegin"></a>Avant de commencer  
**Conditions préalables**  
  
System Center Operations Manager 2007 R2 doit être installé et en cours d’exécution.  
  
Les packs d’administration doivent être installés. Consultez [installer les packs d’administration SCOM &#40;Analytics Platform System&#41;](install-the-scom-management-packs.md).  
  
## <a name="step-1-import-the-sql-server-appliance-base-management-pack"></a><a name="Step1"></a>Étape 1 : importer le pack d’administration de base de l’appliance SQL Server  
  
1.  Ouvrez une session sur l’ordinateur disposant d’un compte appartenant au rôle Administrateurs Operations Manager pour le groupe de gestion Operations Manager 2007.  
  
2.  Dans la console Opérateur, cliquez sur **Administration**.  
  
3.  Cliquez avec le bouton droit sur le nœud **Packs d'administration** , puis cliquez sur **Importer les packs d'administration**.  
  
    ![Cliquez sur Importer les packs d'administration](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP.png "SCOM_IMP")  
  
4.  Dans la liste des packs d’administration, sélectionnez celui que vous voulez importer, cliquez sur **Sélectionner**, puis sur **Ajouter**.  
  
    ![Liste des packs d’administration](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP2.png "SCOM_IMP2")  
  
5.  Recherchez **Appliance** , puis explorez SQL Server base appliance, puis cliquez sur **Ajouter** les deux options.  
  
    ![Base d'appliance SQL Server](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP3.png "SCOM_IMP3")  
  
6.  Une fois que les deux packs d’administration se trouvaient dans le volet inférieur sélectionné, cliquez sur **OK**.  
  
    ![Sélectionnez les deux packs d'administration](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP4.png "SCOM_IMP4")  
  
7.  Cliquez sur **Installer**.  
  
    ![Cliquez sur installer](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP5.png "SCOM_IMP5")  
  
8.  Une fois terminé, cliquez sur **Fermer**.  
  
    ![Une fois l'opération terminée, cliquez sur Fermer](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP6.png "SCOM_IMP6")  
  
## <a name="import-the-monitoring-pack-for-microsoft-sql-server-2008-r2-parallel-data-warehouse-appliance"></a><a name="Step2"></a>Importer le Pack de surveillance pour l’appliance Data Warehouse parallèle Microsoft SQL Server 2008 R2  
  
1.  Cliquez avec le bouton droit sur le nœud **Packs d'administration** , puis cliquez sur **Importer les packs d'administration**.  
  
2.  Choisissez **Ajouter à partir du disque**....  
  
    ![Cliquez avec le bouton droit sur Packs d'administration](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW.png "SCOM_PDW")  
  
3.  Accédez à l’emplacement où vous avez extrait les packs d’administration SQL Server PDW et choisissez les trois packs d’administration qui se trouvent dans la section « packs d’administration sélectionnés à importer ». Pour ce faire, sélectionnez le premier, cliquez sur Maj, puis sélectionnez le dernier. Une fois qu’elles sont toutes sélectionnées, cliquez sur **ouvrir**.  
  
    ![Sélectionner des packs d’administration](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW2.png "SCOM_PDW2")  
  
4.  Cliquez sur **Installer**.  
  
    ![Cliquez sur installer](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW3.png "SCOM_PDW3")  
  
5.  Cliquez sur **Fermer**.  
  
    ![Cliquez sur Fermer](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW4.png "SCOM_PDW4")  
  
## <a name="next-step"></a>étape suivante  
Maintenant que vous avez importé les packs d’administration, passez à l’étape suivante : [configurer SCOM pour surveiller Analytics Platform system &#40;Analytics Platform system&#41;](configure-scom-to-monitor-analytics-platform-system.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
