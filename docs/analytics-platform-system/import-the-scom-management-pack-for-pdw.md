---
title: Importer le Pack d’administration SCOM pour PDW (système de plateforme Analytique)
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
ms.assetid: fa735041-8e58-4886-ae3b-36f3c6298b12
caps.latest.revision: 6
ms.openlocfilehash: d8accd7106cce2274e60793e123779e87b8dfd49
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="import-the-scom-management-pack-for-pdw"></a>Importez le Pack d’administration SCOM pour PDW
Suivez ces étapes pour importer les packs d’administration de System Center Operations Manager (SCOM) pour SQL Server PDW. Les packs d’administration sont requises pour analyser SQL Server PDW de SCOM.  
  
## <a name="BeforeBegin"></a>Avant de commencer  
**Configuration requise**  
  
System Center Operations Manager 2007 R2 doit être installé et en cours d’exécution.  
  
Les packs d’administration doivent être installés. Consultez [installer les Packs d’administration SCOM &#40;système de plateforme Analytique&#41;](install-the-scom-management-packs.md).  
  
## <a name="Step1"></a>Étape 1 : Importer le Pack d’administration de Base SQL Server Appliance  
  
1.  Ouvrez une session l’ordinateur avec un compte qui est membre du rôle Administrateurs Operations Manager pour le groupe d’administration Operations Manager 2007.  
  
2.  Dans la console Opérateur, cliquez sur **Administration**.  
  
3.  Cliquez sur le **packs d’administration** nœud, puis cliquez sur **importer les packs d’administration**.  
  
    ![Cliquez sur Importer les packs d’administration](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP.png "SCOM")  
  
4.  Dans la liste des packs d’administration, sélectionnez le Pack d’administration que vous souhaitez importer, cliquez sur **sélectionnez**, puis cliquez sur **ajouter**.  
  
    ![Liste des packs d’administration](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP2.png "SCOM_IMP2")  
  
5.  Recherchez **Appliance** , puis accédez à la Base d’Appliance SQL Server, puis cliquez **ajouter** les deux options.  
  
    ![Base d’appliance SQL Server](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP3.png "SCOM_IMP3")  
  
6.  Une fois que les deux Packs d’administration ont été dans le volet sélectionné en bas, puis cliquez sur **OK**.  
  
    ![Sélectionnez les packs d’administration](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP4.png "SCOM_IMP4")  
  
7.  Cliquez sur **Installer**.  
  
    ![Cliquez sur Installer](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP5.png "SCOM_IMP5")  
  
8.  Une fois terminé, cliquez sur **fermer**.  
  
    ![Une fois terminé, cliquez sur Fermer](./media/import-the-scom-management-pack-for-pdw/SCOM_IMP6.png "SCOM_IMP6")  
  
## <a name="Step2"></a>Importer le Pack de surveillance pour le matériel de l’entrepôt de données parallèles de Microsoft SQL Server 2008 R2  
  
1.  Cliquez sur le **packs d’administration** nœud, puis cliquez sur **importer les packs d’administration**.  
  
2.  Choisissez **à partir du disque**...  
  
    ![Avec le bouton droit de packs d’administration](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW.png "SCOM_PDW")  
  
3.  Accédez à l’emplacement où vous avez extrait les Packs d’administration SQL Server PDW et choisissez les trois packs d’administration qui se trouvent dans la section « Sélectionnés des packs d’administration pour importer ». Pour cela, en sélectionnant le, en cliquant sur la touche MAJ enfoncée et en sélectionnant le dernier signet. Une fois qu’ils sont tous sélectionnés, cliquez sur **ouvrir**.  
  
    ![Sélectionnez les packs d’administration](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW2.png "SCOM_PDW2")  
  
4.  Cliquez sur **Installer**.  
  
    ![Cliquez sur Installer](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW3.png "SCOM_PDW3")  
  
5.  Cliquez sur **Fermer**.  
  
    ![Cliquez sur Fermer](./media/import-the-scom-management-pack-for-pdw/SCOM_PDW4.png "SCOM_PDW4")  
  
## <a name="next-step"></a>Étape suivante  
Maintenant que vous avez importé les packs d’administration, passez à l’étape suivante : [configurer SCOM pour système de plateforme d’analyse Analytique &#40;système de plateforme Analytique&#41;](configure-scom-to-monitor-analytics-platform-system.md).  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
