---
title: Importer le Pack d’administration SCOM - Analytique Platform System | Microsoft Docs
description: Suivez ces étapes pour importer les packs d’administration de System Center Operations Manager (SCOM) pour Analytique Platform System (APS). Les packs d’administration sont requises pour analyser les Parallel Data Warehouse à partir de SCOM.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: c4280fb257147f3c401badc6eaec18929f6d69b4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149600"
---
# <a name="import-the-scom-management-pack---analytics-platform-system"></a>Importer le Pack d’administration SCOM - Analytique Platform System
Suivez ces étapes pour importer les packs d’administration de System Center Operations Manager (SCOM) pour Analytique Platform System (APS). Les packs d’administration sont requises pour analyser les Parallel Data Warehouse à partir de SCOM. 
  
## <a name="BeforeBegin"></a>Avant de commencer  
**Conditions préalables**  
  
System Center Operations Manager 2007 R2 doit être installé et en cours d’exécution.  
  
Les packs d’administration doivent être installés. Consultez [installer les Packs d’administration SCOM &#40;Analytique Platform System&#41;](install-the-scom-management-packs.md).  
  
## <a name="Step1"></a>Étape 1 : Importer le Pack de gestion de la Base de SQL Server Appliance  
  
1.  Ouvrez une session l’ordinateur avec un compte qui est membre du rôle Administrateurs Operations Manager pour le groupe d’administration Operations Manager 2007.  
  
2.  Dans la console Opérateur, cliquez sur **Administration**.  
  
3.  Cliquez sur le **packs d’administration** nœud, puis cliquez sur **importer les packs d’administration**.  
  
    ![Cliquez sur Importer les packs d’administration](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP.png "SCOM")  
  
4.  Dans la liste des packs d’administration, sélectionnez le pack d’administration que vous souhaitez importer, cliquez sur **sélectionnez**, puis cliquez sur **ajouter**.  
  
    ![Liste des packs d’administration](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP2.png "SCOM_IMP2")  
  
5.  Recherchez **Appliance** , puis accédez à la Base d’Appliance SQL Server, puis cliquez **ajouter** les deux options.  
  
    ![Base d’appliance SQL Server](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP3.png "SCOM_IMP3")  
  
6.  Une fois que les deux packs d’administration ont été dans le volet sélectionné en bas, puis cliquez sur **OK**.  
  
    ![Sélectionnez les deux packs d’administration](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP4.png "SCOM_IMP4")  
  
7.  Cliquez sur **Installer**.  
  
    ![Cliquez sur Installer](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP5.png "SCOM_IMP5")  
  
8.  Une fois terminé, cliquez sur **fermer**.  
  
    ![Une fois terminé, cliquez sur Fermer](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP6.png "SCOM_IMP6")  
  
## <a name="Step2"></a>Importer le Pack de surveillance pour Microsoft SQL Server 2008 R2 Parallel Data Warehouse Appliance  
  
1.  Cliquez sur le **packs d’administration** nœud, puis cliquez sur **importer les packs d’administration**.  
  
2.  Choisissez **à partir du disque**...  
  
    ![Avec le bouton droit de packs d’administration](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW.png "SCOM_PDW")  
  
3.  Accédez à l’emplacement où vous avez extrait les packs d’administration de SQL Server PDW et choisissez les trois packs d’administration qui se trouvent dans la section « Sélectionnés des packs d’administration pour importer ». Pour cela, sélectionnons le premier, en cliquant sur la touche MAJ enfoncée, puis sélectionnez dernier signet. Une fois qu’ils sont tous sélectionnés, cliquez sur **Open**.  
  
    ![Sélectionnez les packs d’administration](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW2.png "SCOM_PDW2")  
  
4.  Cliquez sur **Installer**.  
  
    ![Cliquez sur Installer](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW3.png "SCOM_PDW3")  
  
5.  Cliquez sur **Fermer**.  
  
    ![Cliquez sur Fermer](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW4.png "SCOM_PDW4")  
  
## <a name="next-step"></a>Étape suivante  
Maintenant que vous avez importé les packs d’administration, passez à l’étape suivante : [Configurer SCOM pour surveiller le système de plateforme d’Analytique &#40;Analytique Platform System&#41;](configure-scom-to-monitor-analytics-platform-system.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
