---
title: Spécification de sauvegarde VDI - SQL Server sur Linux | Microsoft Docs
description: Spécification d’Interface périphérique virtuel sauvegarde SQL Server.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 0250ba2b-8cdd-450e-9109-bf74f70e1247
ms.openlocfilehash: 1dab0dcc403a7e0f85cd78e69e9461ef0d566b0c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38006787"
---
# <a name="sql-server-on-linux-vdi-client-sdk-specification"></a>SQL Server sur le client Linux VDI spécification du Kit de développement logiciel

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Ce document décrit les interfaces fournies par le serveur SQL Server sur le SDK de client interface (VDI) Linux appareil virtuel. Éditeurs de logiciels indépendants (ISV) peuvent utiliser le Virtual Backup Device Interface API (Application Programming) pour intégrer SQL Server dans leurs produits. En règle générale, VDI sur Linux se comporte de la même façon et l’infrastructure VDI sur Windows avec les modifications suivantes :

- Mémoire partagée Windows devient la mémoire POSIX partagé.
- Les sémaphores Windows deviennent des sémaphores POSIX.
- Types de Windows comme HRESULT et DWORD sont modifiés en équivalents d’entier.
- Les interfaces COM sont supprimées et remplacées par une paire de Classes C++.
- SQL Server sur Linux ne prend pas en charge les instances nommées pour les références au nom d’instance ont été supprimées. 
- La bibliothèque partagée est implémentée dans libsqlvdi.so installés en /opt/mssql/lib/libsqlvdi.so

Ce document est un complément à **vbackup.chm** qui détaille la spécification d’infrastructure VDI de Windows. Téléchargez le [spécification d’infrastructure VDI de Windows](http://www.microsoft.com/download/details.aspx?id=17282).

Examinez également l’exemple de solution sauvegarde VDI sur le [référentiel GitHub d’exemples SQL Server](http://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sqlvdi-linux).

## <a name="user-permissions-setup"></a>Configuration des autorisations utilisateur

Sur Linux, les primitives POSIX sont détenus par l’utilisateur qui crée les et leur groupe par défaut. Pour les objets créés par SQL Server, ces par défaut appartiendra à l’utilisateur mssql et du groupe mssql. Pour autoriser le partage entre SQL Server et le client VDI, une des deux méthodes suivantes sont recommandées :

1. Exécutez le Client de VDI en tant que l’utilisateur mssql
   
   Exécutez la commande suivante pour basculer vers l’utilisateur mssql :
   
   ```bash
   sudo su mssql
   ```

2. Ajoutez l’utilisateur mssql au groupe de la vdiuser et le vdiuser au groupe mssql.
   
   Exécutez les commandes suivantes :

   ```bash
   sudo useradd vdiuser
   sudo usermod -a -G mssql vdiuser
   sudo usermod -a -G vdiuser mssql
   ```

   Redémarrez le serveur à sélectionner des groupes pour SQL Server et vdiuser

## <a name="client-functions"></a>Fonctions de clients

Ce chapitre contient des descriptions de chacune de ces fonctions du client. Les descriptions incluent les informations suivantes :

- Objectif de la fonction
- Syntaxe de la fonction
- liste de paramètres
- Valeurs retournées
- Notes

## <a name="clientvirtualdevicesetcreate"></a>ClientVirtualDeviceSet::Create

**Objectif** cette fonction crée l’ensemble de l’appareil virtuel.

**Syntaxe**
   ```
   int ClientVirtualDeviceSet::Create (
   char *   name,       // name for the set
   VDConfig   * cfg     // configuration for the set
   );
   ```

| Paramètres | Argument | Explication
| ----- | ----- | ------ |
| | **nom** | Cela identifie l’ensemble de l’appareil virtuel. Les règles pour les noms utilisés par la fonction CreateFileMapping() doivent être suivis. N’importe quel caractère à l’exception de barre oblique inverse (\) peut être utilisé. Il s’agit d’une chaîne de caractères. La chaîne avec le nom de produit ou de la société et le nom de base de données de l’utilisateur en ajoutant le préfixe est recommandé. |
| |**cfg** | Il s’agit de la configuration pour l’ensemble de l’appareil virtuel. Pour plus d’informations, consultez « Configuration » plus loin dans ce document.

| Valeurs de retour | Argument | Explication
| ----- | ----- | ------ |
| |**NOERROR** | La fonction a réussi. |
| |**VD_E_NOTSUPPORTED** |Un ou plusieurs des champs dans la configuration n’est pas valide ou non pris en charge dans le cas contraire. |
| |**VD_E_PROTOCOL** | L’appareil virtuel déjà la valeur existe.

**Remarques** créer une méthode doit être appelée qu’une seule fois par opération BACKUP ou RESTORE. Après avoir appelé la méthode Close, le client peut réutiliser l’interface pour créer un autre ensemble de l’appareil virtuel.

## <a name="clientvirtualdevicesetgetconfiguration"></a>ClientVirtualDeviceSet::GetConfiguration

**Objectif** cette fonction est utilisée pour attendre que le serveur configurer l’ensemble de l’appareil virtuel.
**Syntaxe**
   ```
   int ClientVirtualDeviceSet::GetConfiguration (
   time_t       timeout,    // in milliseconds
   VDConfig *       cfg // selected configuration
   );
   ```

| Paramètres | Argument | Explication
| ----- | ----- | ------ |
| | **Délai d’attente** | Il s’agit du délai d’attente en millisecondes. Utiliser l’infini ou n’importe quel entier négatif pour empêcher le délai d’attente.
| | **cfg** | L’exécution aboutit, il contient la configuration sélectionnée par le serveur. Pour plus d’informations, consultez « Configuration » plus loin dans ce document.

| Valeurs de retour | Argument | Explication
| ----- | ----- | ------ |
| |**NOERROR** | La configuration a été retournée.
| |**VD_E_ABORT** |SignalAbort a été appelée.
| |**VD_E_TIMEOUT** |La fonction a expiré.

**Remarques** cette fonction blocs dans un état critique. Après appel réussi, les appareils dans l’ensemble de l’appareil virtuel peuvent être ouvert.


## <a name="clientvirtualdevicesetopendevice"></a>ClientVirtualDeviceSet::OpenDevice
**Objectif** cette fonction ouvre l’un des appareils dans l’ensemble de l’appareil virtuel.
**Syntaxe**
   ```
   int ClientVirtualDeviceSet::OpenDevice (
   char *           name,       // name for the set
   ClientVirtualDevice **       ppVirtualDevice // returns interface to device
   );
   ```

| Paramètres | Argument | Explication
| ----- | ----- | ------ |
| | **nom** |Cela identifie l’ensemble de l’appareil virtuel.
| | **ppVirtualDevice** |Lorsque la fonction réussit, un pointeur vers l’appareil virtuel est retourné. Cet appareil est utilisé pour la commande GetCommand et CompleteCommand.

| Valeurs de retour | Argument | Explication
| ----- | ----- | ------ |
| |**NOERROR** |La fonction a réussi.
| |**VD_E_ABORT** | Abandon a été demandé.
| |**VD_E_OPEN** |  Tous les appareils sont ouverts.
| |**VD_E_PROTOCOL** |  Le jeu n’est pas dans l’état de l’initialisation ou ce périphérique est déjà ouvert.
| |**VD_E_INVALID** |Le nom de l’appareil n’est pas valide. Il n’est pas un des noms connus devant inclure l’ensemble.

**Remarques** VD_E_OPEN peut être retournée sans problème. Le client peut appeler OpenDevice au moyen d’une boucle jusqu'à ce que ce code est renvoyé.
Si plus d’un appareil configuré, par exemple *n* appareils, l’ensemble de l’appareil virtuel retournera *n* interfaces d’appareil unique.

Le `GetConfiguration` fonction peut être utilisée pour attendre que les appareils peuvent être ouverts.
Si cette fonction n’aboutit pas, une valeur null est retournée via le ppVirtualDevice.
 
## <a name="clientvirtualdevicegetcommand"></a>ClientVirtualDevice::GetCommand

**Objectif** cette fonction est utilisée pour obtenir la prochaine commande en file d’attente à un appareil. Lors de la demande, cette fonction attend que la commande suivante.

**Syntaxe**
   ```
   int ClientVirtualDevice::GetCommand (
   time_t       timeout,    // time-out in milliseconds
   VDC_Command**    ppCmd   // returns the next command
   );
   ```

| Paramètres | Argument | Explication
| ----- | ----- | ------ |
| |**Délai d’attente** |Il s’agit de la durée d’attente, en millisecondes. Utilisez finie pour attendre indéfiniment. Utilisez 0 pour l’interrogation d’une commande. VD_E_TIMEOUT est retournée si aucune commande n’est actuellement disponible. Si le délai d’attente se produit, le client décide de l’action suivante.
| |**Délai d'expiration** |Il s’agit de la durée d’attente, en millisecondes. Utilisez finie ou une valeur négative pour attendre indéfiniment. Utilisez 0 pour l’interrogation d’une commande. VD_E_TIMEOUT est retournée si aucune commande n’est disponible avant l’expiration du délai. Si le délai d’expiration se produit, le client décide de l’action suivante.
| |**ppCmd** |Lorsqu’une commande est retournée avec succès, le paramètre retourne l’adresse d’une commande à exécuter. La mémoire retournée est en lecture seule. Lorsque la commande est terminée, ce pointeur est passé à la routine CompleteCommand. Pour plus d’informations sur chaque commande, consultez « Commandes » plus loin dans ce document.
        
| Valeurs de retour | Argument | Explication
| ----- | ----- | ------ |
| |**NOERROR** |Une commande a été récupérée.
| |**VD_E_CLOSE** |L’appareil a été fermée par le serveur.
| |**VD_E_TIMEOUT** |Aucune commande n’était disponible et le délai d’attente a expiré.
| |**VD_E_ABORT** |Le client ou le serveur a utilisé le SignalAbort pour forcer un arrêt.

**Remarques** VD_E_CLOSE lorsque est retournée, SQL Server a fermé l’appareil. Il s’agit de la partie de l’arrêt normal. Une fois que tous les appareils ont été fermés, le client appelle ClientVirtualDeviceSet::Close pour fermer l’ensemble de l’appareil virtuel.
Lorsque cette routine doit bloquer à attendre une commande, le thread reste dans une condition d’une erreur.

## <a name="clientvirtualdevicecompletecommand"></a>ClientVirtualDevice::CompleteCommand

**Objectif** cette fonction est utilisée pour indiquer à SQL Server qui vient d’une commande. Informations d’achèvement appropriées pour la commande doivent être retournées. Pour plus d’informations, consultez « Commandes » plus loin dans ce document.

**Syntaxe** 

   ```
   int ClientVirtualDevice::CompleteCommand (
   VDC_Command pCmd,        // the command
   int  completionCode,     // completion code
   unsigned long    bytesTransferred,   // bytes transferred
   int64_t  position        // current position
   );
   ```

| Paramètres | Argument | Explication
| ----- | ----- | ------ |
| |**pCmd** |Il s’agit de l’adresse d’une commande précédemment retournée à partir de ClientVirtualDevice::GetCommand.
| |**completionCode** |Il s’agit d’un code d’état qui indique l’état d’achèvement. Ce paramètre doit être retourné pour toutes les commandes. Le code retourné doit convenir à la commande en cours d’exécution. ERROR_SUCCESS est utilisé dans tous les cas pour désigner une commande exécutée avec succès. Pour obtenir la liste complète des codes possibles, consultez le fichier, vdierror.h. Une liste standard des codes d’état pour chaque commande apparaît dans les « Commandes » plus loin dans ce document.
| |**bytesTransferred** |Il s’agit du nombre d’octets transférés avec succès. Celui-ci est renvoyé uniquement pour le transfert de données commandes de lecture et d’écriture.
| |**position** |Il s’agit d’une réponse à la commande GetPosition uniquement.
        
| Valeurs de retour | Argument | Explication
| ----- | ----- | ------ |
| |**NOERROR** |La saisie semi-automatique a été correctement indiqué.
| |**VD_E_INVALID** |pCmd n’était pas une commande active.
| |**VD_E_ABORT** |Abandon a été signalé.
| |**VD_E_PROTOCOL** |L’appareil n’est pas ouvert.

**Remarques** None

## <a name="clientvirtualdevicesetsignalabort"></a>ClientVirtualDeviceSet::SignalAbort

**Objectif** cette fonction est utilisée pour signaler qu’un arrêt anormal doit avoir lieu.

**Syntaxe** 

   ```
   int ClientVirtualDeviceSet::SignalAbort ();
   ```

| Paramètres | Argument | Explication
| ----- | ----- | ------ |
| |None | Non applicable
        
| Valeurs de retour | Argument | Explication
| ----- | ----- | ------ |
| |**NOERROR**|La notification d’annulation a été validée avec succès.

**Remarques** à tout moment, le client peut choisir d’abandonner l’opération de sauvegarde ou de restauration. Cette routine signale que toutes les opérations doivent s’arrêter. L’état de l’ensemble de l’appareil virtuel global entre un état arrête anormalement. Aucune commande supplémentaire n’est retournées sur tous les périphériques. Toutes les commandes non terminées sont renseignés automatiquement, retournant ERROR_OPERATION_ABORTED comme un code d’achèvement. Le client doit appeler ClientVirtualDeviceSet::Close après que qu’il s’est terminée en toute sécurité toute utilisation en suspens de mémoires tampons fournies au client. Pour plus d’informations, consultez « Arrêt anormal » plus haut dans ce document.

## <a name="clientvirtualdevicesetclose"></a>ClientVirtualDeviceSet::Close

**Objectif** cette fonction ferme le jeu de périphérique virtuel créé par ClientVirtualDeviceSet::Create. Il en résulte dans la version de toutes les ressources associées à l’ensemble de l’appareil virtuel.

**Syntaxe** 

   ```
   int ClientVirtualDeviceSet::Close ();
   ```

| Paramètres | Argument | Explication
| ----- | ----- | ------ |
| |None |Non applicable
        
| Valeurs de retour | Argument | Explication
| ----- | ----- | ------ |
| |**NOERROR** |Il est renvoyé lorsque l’ensemble de l’appareil virtuel a été correctement fermée.
| |**VD_E_PROTOCOL** |Aucune action n’a été effectuée, car l’ensemble de l’appareil virtuel n’est pas ouvert.
| |**VD_E_OPEN** |Appareils étaient toujours ouverts.

**Remarques** l’appel de Close est une déclaration de client que toutes les ressources utilisées par l’ensemble de l’appareil virtuel doivent être libérées. Le client doit s’assurer que toutes les activités impliquant des mémoires tampons de données et les appareils virtuels se termine avant l’appel de Close. Toutes les interfaces de périphérique virtuel retournés par OpenDevice sont invalidées par fermer.
Le client est autorisé à émettre un appel de création sur l’interface de jeu de périphérique virtuel une fois que l’appel de Close est renvoyé. Un tel appel créerait un nouvel appareil virtuel défini pour une opération de sauvegarde ou de restauration ultérieure.
Si vous fermez est appelée lorsqu’un ou plusieurs appareils virtuels sont toujours ouverts, VD_E_OPEN est retournée. Dans ce cas, SignalAbort est déclenchée en interne, pour garantir un arrêt correct si possible. Ressources d’infrastructure VDI sont libérées. Le client doit attendre pour obtenir une indication VD_E_CLOSE sur chaque appareil avant d’appeler ClientVirtualDeviceSet::Close. Si le client sait que l’ensemble de l’appareil virtuel est déjà dans un état arrête anormalement, puis il ne doit pas attendre une indication VD_E_CLOSE à partir de la commande GetCommand et que vous pouvez appeler ClientVirtualDeviceSet::Close dès que l’activité sur les mémoires tampons partagés est terminée.
Pour plus d’informations, consultez « Arrêt anormal » plus haut dans ce document.

## <a name="clientvirtualdevicesetopeninsecondary"></a>ClientVirtualDeviceSet::OpenInSecondary

**Objectif** cette fonction ouvre le périphérique virtuel défini dans un client secondaire. Le client principal doit ont déjà utilisé Create and GetConfiguration pour configurer l’ensemble de l’appareil virtuel.

**Syntaxe** 
   
   ```
   int ClientVirtualDeviceSet::OpenInSecondary (
   char *   setName         // name of the set
   );
   ```

| Paramètres | Argument | Explication
| ----- | ----- | ------ |
| |**setName** |Cela identifie le jeu. Ce nom respecte la casse et doit correspondre au nom utilisé par le client principal lorsqu’il appelé ClientVirtualDeviceSet::Create.

| Valeurs de retour | Argument | Explication
| ----- | ----- | ------ |
| |**NOERROR** |La fonction a réussi.
| |**VD_E_PROTOCOL** |L’ensemble de l’appareil virtuel n’a pas été créé, a déjà été ouverte sur ce client, ou l’appareil virtuel jeu n’est pas prêt à accepter les demandes en cours à partir de clients secondaire.
| |**VD_E_ABORT** |L’opération est en cours d’abandon.

**Remarques** lorsque vous utilisez un modèle de processus multiples, le client principal est chargé de détecter un arrêt normaux et anormaux de clients secondaire.

## <a name="clientvirtualdevicesetgetbufferhandle"></a>ClientVirtualDeviceSet::GetBufferHandle

**Objectif** certaines applications peuvent nécessiter plus d’un processus de fonctionner sur les mémoires tampons retournés par ClientVirtualDevice::GetCommand. Dans ce cas, le processus qui reçoit la commande peut utiliser GetBufferHandle pour obtenir un handle de processus indépendants qui identifie la mémoire tampon. Ce handle peut ensuite être communiqué à tout autre processus qui possède également l’ouvrir même périphérique virtuel défini. Ce processus serait ensuite utiliser ClientVirtualDeviceSet::MapBufferHandle pour obtenir l’adresse de la mémoire tampon. L’adresse sera probablement une adresse différente de celle de son partenaire, car chaque processus peuvent mapper des mémoires tampons à différentes adresses.

**Syntaxe** 

   ```
   int ClientVirtualDeviceSet::GetBufferHandle (
   uint8_t*     pBuffer,        // in: buffer address
   unsigned int*        pBufferHandle   // out: buffer handle
   );
   ```

| Paramètres | Argument | Explication
| ----- | ----- | ------ |
| |**pBuffer** |Il s’agit de l’adresse d’une mémoire tampon obtenue à partir d’une commande de lecture ou d’écriture.
| |**BufferHandle** |Identificateur unique pour la mémoire tampon est retourné.

| Valeurs de retour | Argument | Explication
| ----- | ----- | ------ |
| |**NOERROR** |La fonction a réussi.
| |**VD_E_PROTOCOL** |L’ensemble de l’appareil virtuel n’est pas actuellement ouvert.
| |**VD_E_INVALID** |PBuffer n’est pas une adresse valide.
Remarques le processus qui appelle la fonction GetBufferHandle est chargé d’appeler ClientVirtualDevice::CompleteCommand lorsque le transfert de données est terminé.

## <a name="clientvirtualdevicesetmapbufferhandle"></a>ClientVirtualDeviceSet::MapBufferHandle

**Objectif** cette fonction est utilisée pour obtenir une adresse de mémoire tampon valide à partir d’un handle de mémoire tampon obtenu à partir d’un autre processus. 

**Syntaxe** 

   ```
   int ClientVirtualDeviceSet::MapBufferHandle (
   i        nt  dwBuffer,   // in: buffer handle
   uint8_t**    ppBuffer        // out: buffer address
   );
   ```

| Paramètres | Argument | Explication
| ----- | ----- | ------ |
| |**dwBuffer** |Il s’agit le handle retourné par ClientVirtualDeviceSet::GetBufferHandle.
| |**ppBuffer** |Il s’agit de l’adresse de la mémoire tampon qui est valide dans le processus en cours.

| Valeurs de retour | Argument | Explication
| ----- | ----- | ------ |
| |**NOERROR** |La fonction a réussi.
| |**VD_E_PROTOCOL** |L’ensemble de l’appareil virtuel n’est pas actuellement ouvert.
| |**VD_E_INVALID** |Le ppBuffer est un handle non valide.

**Remarques** doit veiller à communiquer les handles correctement. Handles sont locales à un ensemble de l’appareil virtuel unique. Les processus de partenaire partage un handle doivent s’assurer de cette mémoire tampon les handles sont utilisées uniquement dans l’étendue de l’appareil virtuel défini à partir duquel la mémoire tampon a été obtenue à l’origine.


