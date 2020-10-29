---
title: Informations de référence sur les API du portail d’appareil
description: Informations de référence sur l’API pour le portail de périphériques Windows sur HoloLens
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, portail des appareils Windows, API
ms.openlocfilehash: 6b8f99fbc6f1965639ceef218f5c516d2e6ba467
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679306"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="c83f3-104">Informations de référence sur les API du portail d’appareil</span><span class="sxs-lookup"><span data-stu-id="c83f3-104">Device portal API reference</span></span>

<span data-ttu-id="c83f3-105">Tout ce qui se trouve dans le [portail de périphériques Windows](using-the-windows-device-portal.md) repose sur des API REST que vous pouvez utiliser pour accéder aux données et contrôler votre appareil par programme.</span><span class="sxs-lookup"><span data-stu-id="c83f3-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="c83f3-106">Déploiement de l’application</span><span class="sxs-lookup"><span data-stu-id="c83f3-106">App deloyment</span></span>

<span data-ttu-id="c83f3-107">**/API/App/packagemanager/package (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="c83f3-108">Désinstalle une application</span><span class="sxs-lookup"><span data-stu-id="c83f3-108">Uninstalls an app</span></span>

<span data-ttu-id="c83f3-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-109">Parameters</span></span>
* <span data-ttu-id="c83f3-110">Package : nom de fichier du package à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="c83f3-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="c83f3-111">**/API/App/packagemanager/package (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="c83f3-112">Installe une application</span><span class="sxs-lookup"><span data-stu-id="c83f3-112">Installs an App</span></span>

<span data-ttu-id="c83f3-113">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-113">Parameters</span></span>
* <span data-ttu-id="c83f3-114">Package : nom de fichier du package à installer.</span><span class="sxs-lookup"><span data-stu-id="c83f3-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="c83f3-115">Payload</span><span class="sxs-lookup"><span data-stu-id="c83f3-115">Payload</span></span>
* <span data-ttu-id="c83f3-116">corps http en plusieurs parties, conforme</span><span class="sxs-lookup"><span data-stu-id="c83f3-116">multi-part conforming http body</span></span>

<span data-ttu-id="c83f3-117">**/API/App/packagemanager/packages (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="c83f3-118">Récupère la liste des applications installées sur le système, avec les détails</span><span class="sxs-lookup"><span data-stu-id="c83f3-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="c83f3-119">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="c83f3-119">Return data</span></span>
* <span data-ttu-id="c83f3-120">Liste des packages installés avec des détails</span><span class="sxs-lookup"><span data-stu-id="c83f3-120">List of installed packages with details</span></span>

<span data-ttu-id="c83f3-121">**/API/App/packagemanager/State (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="c83f3-122">Obtient l’état de l’installation de l’application en cours</span><span class="sxs-lookup"><span data-stu-id="c83f3-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="c83f3-123">Collection de vidages</span><span class="sxs-lookup"><span data-stu-id="c83f3-123">Dump collection</span></span>

<span data-ttu-id="c83f3-124">**/API/Debug/dump/usermode/CrashControl (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="c83f3-125">Désactive la collecte de vidages sur incident pour une application faisant</span><span class="sxs-lookup"><span data-stu-id="c83f3-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="c83f3-126">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-126">Parameters</span></span>
* <span data-ttu-id="c83f3-127">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="c83f3-127">packageFullname : package name</span></span>

<span data-ttu-id="c83f3-128">**/API/Debug/dump/usermode/CrashControl (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="c83f3-129">Obtient les paramètres de la collection de vidages sur incident des applications faisant</span><span class="sxs-lookup"><span data-stu-id="c83f3-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="c83f3-130">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-130">Parameters</span></span>
* <span data-ttu-id="c83f3-131">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="c83f3-131">packageFullname : package name</span></span>

<span data-ttu-id="c83f3-132">**/API/Debug/dump/usermode/CrashControl (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="c83f3-133">Active et définit les paramètres de contrôle de vidage pour une application faisant</span><span class="sxs-lookup"><span data-stu-id="c83f3-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="c83f3-134">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-134">Parameters</span></span>
* <span data-ttu-id="c83f3-135">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="c83f3-135">packageFullname : package name</span></span>

<span data-ttu-id="c83f3-136">**/API/Debug/dump/usermode/crashdump (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="c83f3-137">Supprime un vidage sur incident pour une application faisant</span><span class="sxs-lookup"><span data-stu-id="c83f3-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="c83f3-138">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-138">Parameters</span></span>
* <span data-ttu-id="c83f3-139">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="c83f3-139">packageFullname : package name</span></span>
* <span data-ttu-id="c83f3-140">fileName : nom du fichier dump</span><span class="sxs-lookup"><span data-stu-id="c83f3-140">fileName : dump file name</span></span>

<span data-ttu-id="c83f3-141">**/API/Debug/dump/usermode/crashdump (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="c83f3-142">Récupère un vidage sur incident pour une application faisant</span><span class="sxs-lookup"><span data-stu-id="c83f3-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="c83f3-143">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-143">Parameters</span></span>
* <span data-ttu-id="c83f3-144">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="c83f3-144">packageFullname : package name</span></span>
* <span data-ttu-id="c83f3-145">fileName : nom du fichier dump</span><span class="sxs-lookup"><span data-stu-id="c83f3-145">fileName : dump file name</span></span>

<span data-ttu-id="c83f3-146">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="c83f3-146">Return data</span></span>
* <span data-ttu-id="c83f3-147">Fichier dump.</span><span class="sxs-lookup"><span data-stu-id="c83f3-147">Dump file.</span></span> <span data-ttu-id="c83f3-148">Inspecter avec WinDbg ou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c83f3-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="c83f3-149">**/API/Debug/dump/usermode/dumps (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="c83f3-150">Retourne la liste de tous les vidages sur incident pour les applications faisant</span><span class="sxs-lookup"><span data-stu-id="c83f3-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="c83f3-151">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="c83f3-151">Return data</span></span>
* <span data-ttu-id="c83f3-152">Liste des vidages sur incident par application à chargement latéral</span><span class="sxs-lookup"><span data-stu-id="c83f3-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="c83f3-153">ETW</span><span class="sxs-lookup"><span data-stu-id="c83f3-153">ETW</span></span>

<span data-ttu-id="c83f3-154">**/API/ETW/Providers (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="c83f3-155">Énumère les fournisseurs inscrits</span><span class="sxs-lookup"><span data-stu-id="c83f3-155">Enumerates registered providers</span></span>

<span data-ttu-id="c83f3-156">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="c83f3-156">Return data</span></span>
* <span data-ttu-id="c83f3-157">Liste des fournisseurs, nom convivial et GUID</span><span class="sxs-lookup"><span data-stu-id="c83f3-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="c83f3-158">**/API/ETW/session/Realtime (obtient/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="c83f3-159">Crée une session ETW en temps réel ; géré sur un WebSocket.</span><span class="sxs-lookup"><span data-stu-id="c83f3-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="c83f3-160">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="c83f3-160">Return data</span></span>
* <span data-ttu-id="c83f3-161">Événements ETW des fournisseurs activés</span><span class="sxs-lookup"><span data-stu-id="c83f3-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="c83f3-162">Système d’exploitation holographique</span><span class="sxs-lookup"><span data-stu-id="c83f3-162">Holographic OS</span></span>

<span data-ttu-id="c83f3-163">**/API/Holographic/OS/ETW/customproviders (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="c83f3-164">Retourne une liste de fournisseurs ETW spécifiques à HoloLens qui ne sont pas inscrits auprès du système.</span><span class="sxs-lookup"><span data-stu-id="c83f3-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="c83f3-165">**/API/Holographic/OS/services (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="c83f3-166">Retourne les États de tous les services en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c83f3-166">Returns the states of all services running.</span></span>

<span data-ttu-id="c83f3-167">**/API/Holographic/OS/Settings/IPD (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="c83f3-168">Obtient la IPD stockée (distance interpupillary) en millimètres.</span><span class="sxs-lookup"><span data-stu-id="c83f3-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="c83f3-169">**/API/Holographic/OS/Settings/IPD (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="c83f3-170">Définit l’IPD</span><span class="sxs-lookup"><span data-stu-id="c83f3-170">Sets the IPD</span></span>

<span data-ttu-id="c83f3-171">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-171">Parameters</span></span>
* <span data-ttu-id="c83f3-172">IPD : nouvelle valeur IPD à définir en millimètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="c83f3-173">**/API/Holographic/OS/webmanagement/Settings/HTTPS (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="c83f3-174">Obtenir la spécification HTTPS pour Device Portal</span><span class="sxs-lookup"><span data-stu-id="c83f3-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="c83f3-175">**/API/Holographic/OS/webmanagement/Settings/HTTPS (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="c83f3-176">Définit les exigences HTTPs pour le portail de l’appareil</span><span class="sxs-lookup"><span data-stu-id="c83f3-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="c83f3-177">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-177">Parameters</span></span>
* <span data-ttu-id="c83f3-178">obligatoire : Oui, non ou par défaut</span><span class="sxs-lookup"><span data-stu-id="c83f3-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="c83f3-179">Perception holographique</span><span class="sxs-lookup"><span data-stu-id="c83f3-179">Holographic Perception</span></span>

<span data-ttu-id="c83f3-180">**/API/Holographic/perception/client (obtient/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="c83f3-181">Accepte les mises à niveau de WebSocket et exécute un client de perception qui envoie des mises à jour à 30 i/s.</span><span class="sxs-lookup"><span data-stu-id="c83f3-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="c83f3-182">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-182">Parameters</span></span>
* <span data-ttu-id="c83f3-183">Clientmode : "active" force le mode de suivi visuel lorsqu’il ne peut pas être établi passivement</span><span class="sxs-lookup"><span data-stu-id="c83f3-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="c83f3-184">Thermique holographique</span><span class="sxs-lookup"><span data-stu-id="c83f3-184">Holographic Thermal</span></span>

<span data-ttu-id="c83f3-185">**/API/Holographic/thermal/stage (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="c83f3-186">Récupération de l’étape thermique de l’appareil (0 normal, 1 chaud, 2 critique)</span><span class="sxs-lookup"><span data-stu-id="c83f3-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="c83f3-187">Gestionnaire de cartes</span><span class="sxs-lookup"><span data-stu-id="c83f3-187">Map Manager</span></span>

<span data-ttu-id="c83f3-188">**/api/holographic/mapmanager/mapFiles (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="c83f3-189">Obtient la liste des fichiers de mappage disponibles (. MapX).</span><span class="sxs-lookup"><span data-stu-id="c83f3-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="c83f3-190">**/api/holographic/mapmanager/anchorFiles (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="c83f3-191">Obtient la liste des fichiers d’ancrage disponibles (. ancx).</span><span class="sxs-lookup"><span data-stu-id="c83f3-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="c83f3-192">**/api/holographic/mapmanager/srdbFiles (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="c83f3-193">Obtient la liste des fichiers de base de données de reconstruction spatiale disponibles (. srdb).</span><span class="sxs-lookup"><span data-stu-id="c83f3-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="c83f3-194">**/API/Holographic/mapmanager/getanchors (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="c83f3-195">Obtient la liste des ancres persistantes pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="c83f3-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="c83f3-196">Télécharger/Télécharger/supprimer des fichiers</span><span class="sxs-lookup"><span data-stu-id="c83f3-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="c83f3-197">**/API/Holographic/mapmanager/Download (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="c83f3-198">Télécharge un fichier de base de données de carte, d’ancrage ou de reconstruction spatiale.</span><span class="sxs-lookup"><span data-stu-id="c83f3-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="c83f3-199">Le fichier doit avoir été préalablement téléchargé ou exporté.</span><span class="sxs-lookup"><span data-stu-id="c83f3-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="c83f3-200">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-200">Parameters</span></span>
* <span data-ttu-id="c83f3-201">FileName : nom du fichier à télécharger.</span><span class="sxs-lookup"><span data-stu-id="c83f3-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="c83f3-202">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c83f3-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="c83f3-203">**/API/Holographic/mapmanager/upload (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="c83f3-204">Charge un fichier de base de données de carte, d’ancrage ou de reconstruction spatiale.</span><span class="sxs-lookup"><span data-stu-id="c83f3-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="c83f3-205">Une fois qu’un fichier est chargé, il peut être importé ultérieurement pour être utilisé par le système.</span><span class="sxs-lookup"><span data-stu-id="c83f3-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="c83f3-206">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-206">Parameters</span></span>
* <span data-ttu-id="c83f3-207">fichier : nom du fichier à charger.</span><span class="sxs-lookup"><span data-stu-id="c83f3-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="c83f3-208">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c83f3-208">Example:</span></span>
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

<span data-ttu-id="c83f3-209">**/API/Holographic/mapmanager/Delete (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="c83f3-210">Supprime un fichier de base de données de carte, d’ancrage ou de reconstruction spatiale.</span><span class="sxs-lookup"><span data-stu-id="c83f3-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="c83f3-211">Le fichier doit avoir été préalablement téléchargé ou exporté.</span><span class="sxs-lookup"><span data-stu-id="c83f3-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="c83f3-212">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-212">Parameters</span></span>
* <span data-ttu-id="c83f3-213">FileName : nom du fichier à supprimer.</span><span class="sxs-lookup"><span data-stu-id="c83f3-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="c83f3-214">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c83f3-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="c83f3-215">Exporter</span><span class="sxs-lookup"><span data-stu-id="c83f3-215">Export</span></span>

<span data-ttu-id="c83f3-216">**/API/Holographic/mapmanager/Export (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="c83f3-217">Exporte le mappage actuellement utilisé par le système.</span><span class="sxs-lookup"><span data-stu-id="c83f3-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="c83f3-218">Une fois exportée, elle peut être téléchargée.</span><span class="sxs-lookup"><span data-stu-id="c83f3-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="c83f3-219">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c83f3-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="c83f3-220">**/API/Holographic/mapmanager/exportanchors (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="c83f3-221">Exporte le mappage actuellement utilisé par le système.</span><span class="sxs-lookup"><span data-stu-id="c83f3-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="c83f3-222">Une fois exportée, elle peut être téléchargée.</span><span class="sxs-lookup"><span data-stu-id="c83f3-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="c83f3-223">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c83f3-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="c83f3-224">**/API/Holographic/mapmanager/exportmapandanchors (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="c83f3-225">Exporte le mappage et les ancres actuellement utilisés par le système.</span><span class="sxs-lookup"><span data-stu-id="c83f3-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="c83f3-226">Une fois exportés, ils peuvent être téléchargés.</span><span class="sxs-lookup"><span data-stu-id="c83f3-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="c83f3-227">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c83f3-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="c83f3-228">**/API/Holographic/mapmanager/exportmapandspatialmappingdb (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="c83f3-229">Exporte le mappage et la base de données de reconstruction spatiale actuellement utilisés par le système.</span><span class="sxs-lookup"><span data-stu-id="c83f3-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="c83f3-230">Une fois qu’elles sont exportées, elles peuvent être téléchargées.</span><span class="sxs-lookup"><span data-stu-id="c83f3-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="c83f3-231">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c83f3-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="c83f3-232">Importer</span><span class="sxs-lookup"><span data-stu-id="c83f3-232">Import</span></span>

<span data-ttu-id="c83f3-233">**/API/Holographic/mapmanager/Import (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="c83f3-234">Indique au système le mappage qui doit être utilisé actuellement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="c83f3-235">Peut être appelé sur des fichiers qui ont été exportés ou téléchargés.</span><span class="sxs-lookup"><span data-stu-id="c83f3-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="c83f3-236">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-236">Parameters</span></span>
* <span data-ttu-id="c83f3-237">Nom de fichier : nom de la carte à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c83f3-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="c83f3-238">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c83f3-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="c83f3-239">**/API/Holographic/mapmanager/importanchors (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="c83f3-240">Indique au système les ancres à utiliser actuellement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="c83f3-241">Peut être appelé sur des fichiers qui ont été exportés ou téléchargés.</span><span class="sxs-lookup"><span data-stu-id="c83f3-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="c83f3-242">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-242">Parameters</span></span>
* <span data-ttu-id="c83f3-243">Nom de fichier : nom des ancres à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c83f3-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="c83f3-244">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c83f3-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="c83f3-245">**/API/Holographic/mapmanager/importspatialmappingdb (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="c83f3-246">Indique au système la base de données de reconstruction spatiale à utiliser actuellement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="c83f3-247">Peut être appelé sur des fichiers qui ont été exportés ou téléchargés.</span><span class="sxs-lookup"><span data-stu-id="c83f3-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="c83f3-248">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-248">Parameters</span></span>
* <span data-ttu-id="c83f3-249">Nom de fichier : nom de la base de connaissances de mappage spatiale à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c83f3-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="c83f3-250">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c83f3-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="c83f3-251">Autres</span><span class="sxs-lookup"><span data-stu-id="c83f3-251">Other</span></span>

<span data-ttu-id="c83f3-252">**/API/Holographic/mapmanager/resetmapandanchorsandsrdb (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="c83f3-253">Réinitialisez le système pour la carte, les ancres et la base de données de reconstruction spatiale.</span><span class="sxs-lookup"><span data-stu-id="c83f3-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="c83f3-254">Exemple :</span><span class="sxs-lookup"><span data-stu-id="c83f3-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="c83f3-255">**/API/Holographic/mapmanager/Status (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="c83f3-256">Obtient l’état du système, notamment les fichiers de base de données de mappage, d’ancrage et de reconstruction spatiale qui ont été importés pour la dernière fois.</span><span class="sxs-lookup"><span data-stu-id="c83f3-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="c83f3-257">MRC (Mixed Reality Capture)</span><span class="sxs-lookup"><span data-stu-id="c83f3-257">Mixed Reality Capture</span></span>

<span data-ttu-id="c83f3-258">**/API/Holographic/MRC/file (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="c83f3-259">Télécharge un fichier de réalité mixte à partir de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="c83f3-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="c83f3-260">Utilisez le paramètre de requête op = Stream pour la diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="c83f3-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="c83f3-261">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-261">Parameters</span></span>
* <span data-ttu-id="c83f3-262">nom de fichier : nom, hex64 encodé, du fichier vidéo à récupérer</span><span class="sxs-lookup"><span data-stu-id="c83f3-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="c83f3-263">OP : flux</span><span class="sxs-lookup"><span data-stu-id="c83f3-263">op : stream</span></span>

<span data-ttu-id="c83f3-264">**/API/Holographic/MRC/file (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="c83f3-265">Supprime un enregistrement de la réalité mixte de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="c83f3-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="c83f3-266">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-266">Parameters</span></span>
* <span data-ttu-id="c83f3-267">nom de fichier : nom, hex64 encodé, du fichier à supprimer</span><span class="sxs-lookup"><span data-stu-id="c83f3-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="c83f3-268">**/API/Holographic/MRC/Files (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="c83f3-269">Retourne la liste des fichiers de réalité mixte stockés sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="c83f3-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="c83f3-270">**/API/Holographic/MRC/photo (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="c83f3-271">Prend une photo de réalité mixte et crée un fichier sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="c83f3-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="c83f3-272">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-272">Parameters</span></span>
* <span data-ttu-id="c83f3-273">Holo : capturer les hologrammes : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="c83f3-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="c83f3-274">PV : capturer l’appareil photo PV : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="c83f3-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="c83f3-275">RenderFromCamera : (HoloLens 2 uniquement) rendu du point de vue de la caméra photo/vidéo : true ou false (true par défaut)</span><span class="sxs-lookup"><span data-stu-id="c83f3-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="c83f3-276">**/API/Holographic/MRC/Settings (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="c83f3-277">Obtient les paramètres de capture de la réalité mixte par défaut</span><span class="sxs-lookup"><span data-stu-id="c83f3-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="c83f3-278">**/API/Holographic/MRC/Settings (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="c83f3-279">Définit les paramètres de capture de la réalité mixte par défaut.</span><span class="sxs-lookup"><span data-stu-id="c83f3-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="c83f3-280">Certains de ces paramètres sont appliqués à la photo et à la capture de vidéo MRC du système.</span><span class="sxs-lookup"><span data-stu-id="c83f3-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="c83f3-281">**/API/Holographic/MRC/Status (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="c83f3-282">Obtient l’état de capture de la réalité mixte dans le portail de périphériques Windows.</span><span class="sxs-lookup"><span data-stu-id="c83f3-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="c83f3-283">***Réponse***</span><span class="sxs-lookup"><span data-stu-id="c83f3-283">***Response***</span></span>

<span data-ttu-id="c83f3-284">La réponse contient une propriété JSON indiquant si le portail de périphériques Windows enregistre ou non une vidéo.</span><span class="sxs-lookup"><span data-stu-id="c83f3-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="c83f3-285">**/API/Holographic/MRC/thumbnail (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-285">**/api/holographic/mrc/thumbnail (GET)**</span></span>

<span data-ttu-id="c83f3-286">Obtient l’image miniature pour le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="c83f3-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="c83f3-287">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-287">Parameters</span></span>
* <span data-ttu-id="c83f3-288">nom de fichier : nom, hex64 encodé, du fichier pour lequel la miniature est demandée.</span><span class="sxs-lookup"><span data-stu-id="c83f3-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="c83f3-289">**/API/Holographic/MRC/Video/Control/Start (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="c83f3-290">Démarre un enregistrement de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="c83f3-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="c83f3-291">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-291">Parameters</span></span>
* <span data-ttu-id="c83f3-292">Holo : capturer les hologrammes : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="c83f3-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="c83f3-293">PV : capturer l’appareil photo PV : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="c83f3-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="c83f3-294">MIC : capturer le microphone : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="c83f3-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="c83f3-295">loopback : capturer l’audio de l’application : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="c83f3-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="c83f3-296">RenderFromCamera : (HoloLens 2 uniquement) rendu du point de vue de la caméra photo/vidéo : true ou false (true par défaut)</span><span class="sxs-lookup"><span data-stu-id="c83f3-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="c83f3-297">Vstab : (HoloLens 2 uniquement) activer la stabilisation vidéo : true ou false (true par défaut)</span><span class="sxs-lookup"><span data-stu-id="c83f3-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="c83f3-298">vstabbuffer : (HoloLens 2 uniquement) latence de la mémoire tampon de stabilisation vidéo : de 0 à 30 frames (15 images par défaut)</span><span class="sxs-lookup"><span data-stu-id="c83f3-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="c83f3-299">**/API/Holographic/MRC/Video/Control/Stop (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="c83f3-300">Arrête l’enregistrement de la réalité mixte actuelle</span><span class="sxs-lookup"><span data-stu-id="c83f3-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="c83f3-301">Diffusion en continu de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="c83f3-301">Mixed Reality Streaming</span></span>

<span data-ttu-id="c83f3-302">HoloLens prend en charge l’aperçu instantané de la réalité mixte via le téléchargement segmenté d’un MP4 fragmenté.</span><span class="sxs-lookup"><span data-stu-id="c83f3-302">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="c83f3-303">Les flux de réalité mixte partagent le même ensemble de paramètres pour contrôler ce qui est capturé :</span><span class="sxs-lookup"><span data-stu-id="c83f3-303">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="c83f3-304">Holo : capturer les hologrammes : true ou false</span><span class="sxs-lookup"><span data-stu-id="c83f3-304">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="c83f3-305">PV : capturer l’appareil photo PV : true ou false</span><span class="sxs-lookup"><span data-stu-id="c83f3-305">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="c83f3-306">MIC : capturer le microphone : true ou false</span><span class="sxs-lookup"><span data-stu-id="c83f3-306">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="c83f3-307">loopback : capturer l’audio de l’application : true ou false</span><span class="sxs-lookup"><span data-stu-id="c83f3-307">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="c83f3-308">Si aucun de ces éléments n’est spécifié : les hologrammes, la caméra photo/vidéo et l’audio de l’application sont capturés</span><span class="sxs-lookup"><span data-stu-id="c83f3-308">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="c83f3-309">Si des paramètres sont spécifiés : les paramètres non spécifiés ont par défaut la valeur false</span><span class="sxs-lookup"><span data-stu-id="c83f3-309">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="c83f3-310">Paramètres facultatifs (HoloLens 2 uniquement)</span><span class="sxs-lookup"><span data-stu-id="c83f3-310">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="c83f3-311">RenderFromCamera : rendu du point de vue de la caméra photo/vidéo : true ou false (true par défaut)</span><span class="sxs-lookup"><span data-stu-id="c83f3-311">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="c83f3-312">Vstab : activer la stabilisation vidéo : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="c83f3-312">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="c83f3-313">vstabbuffer : latence de la mémoire tampon de stabilisation vidéo : de 0 à 30 frames (15 images par défaut)</span><span class="sxs-lookup"><span data-stu-id="c83f3-313">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="c83f3-314">**/API/Holographic/Stream/live.mp4 (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-314">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="c83f3-315">Un flux 1280x720p 30fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="c83f3-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="c83f3-316">**/API/Holographic/Stream/live_high.mp4 (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-316">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="c83f3-317">Un flux 1280x720p 30fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="c83f3-317">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="c83f3-318">**/API/Holographic/Stream/live_med.mp4 (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-318">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="c83f3-319">Flux 854x480p 30fps 2,5 Mbits.</span><span class="sxs-lookup"><span data-stu-id="c83f3-319">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="c83f3-320">**/API/Holographic/Stream/live_low.mp4 (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-320">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="c83f3-321">Flux 428x240p 15fps 0,6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="c83f3-321">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="c83f3-322">Mise en réseau</span><span class="sxs-lookup"><span data-stu-id="c83f3-322">Networking</span></span>

<span data-ttu-id="c83f3-323">**/API/Networking/ipconfig (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-323">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="c83f3-324">Obtient la configuration IP actuelle</span><span class="sxs-lookup"><span data-stu-id="c83f3-324">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="c83f3-325">Informations sur le système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="c83f3-325">OS Information</span></span>

<span data-ttu-id="c83f3-326">**/API/OS/info (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-326">**/api/os/info (GET)**</span></span>

<span data-ttu-id="c83f3-327">Obtient des informations sur le système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="c83f3-327">Gets operating system information</span></span>

<span data-ttu-id="c83f3-328">**/API/OS/MachineName (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-328">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="c83f3-329">Obtient le nom de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="c83f3-329">Gets the machine name</span></span>

<span data-ttu-id="c83f3-330">**/API/OS/MachineName (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-330">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="c83f3-331">Définit le nom de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="c83f3-331">Sets the machine name</span></span>

<span data-ttu-id="c83f3-332">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-332">Parameters</span></span>
* <span data-ttu-id="c83f3-333">nom : nouveau nom de l’ordinateur, hex64 encodé, à affecter à</span><span class="sxs-lookup"><span data-stu-id="c83f3-333">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="c83f3-334">Contrôle de simulation de perception</span><span class="sxs-lookup"><span data-stu-id="c83f3-334">Perception Simulation Control</span></span>

<span data-ttu-id="c83f3-335">**/API/Holographic/simulation/Control/mode (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-335">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="c83f3-336">Obtient le mode de simulation</span><span class="sxs-lookup"><span data-stu-id="c83f3-336">Get the simulation mode</span></span>

<span data-ttu-id="c83f3-337">**/API/Holographic/simulation/Control/mode (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-337">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="c83f3-338">Définir le mode de simulation</span><span class="sxs-lookup"><span data-stu-id="c83f3-338">Set the simulation mode</span></span>

<span data-ttu-id="c83f3-339">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-339">Parameters</span></span>
* <span data-ttu-id="c83f3-340">mode : mode de simulation : par défaut, simulation, distant, hérité</span><span class="sxs-lookup"><span data-stu-id="c83f3-340">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="c83f3-341">**/API/Holographic/simulation/Control/Stream (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-341">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="c83f3-342">Supprimer un flux de contrôle.</span><span class="sxs-lookup"><span data-stu-id="c83f3-342">Delete a control stream.</span></span>

<span data-ttu-id="c83f3-343">**/API/Holographic/simulation/Control/Stream (obtient/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-343">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="c83f3-344">Ouvrez une connexion de socket Web pour un flux de contrôle.</span><span class="sxs-lookup"><span data-stu-id="c83f3-344">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="c83f3-345">**/API/Holographic/simulation/Control/Stream (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-345">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="c83f3-346">Créez un flux de contrôle (priorité obligatoire) ou publiez des données dans un flux créé (streamId requis).</span><span class="sxs-lookup"><span data-stu-id="c83f3-346">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="c83f3-347">Les données publiées sont supposées être de type « application/octet-stream ».</span><span class="sxs-lookup"><span data-stu-id="c83f3-347">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="c83f3-348">**/API/Holographic/Simulation/Display/Stream (obtient/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-348">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="c83f3-349">Demandez un flux vidéo de simulation contenant le contenu affiché sur le système lorsqu’il est en mode « simulation ».</span><span class="sxs-lookup"><span data-stu-id="c83f3-349">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="c83f3-350">Un en-tête de descripteur de format simple sera envoyé initialement, suivi des textures encodées H. 264, chacune précédée d’un en-tête indiquant l’index oculaire et la taille de la texture.</span><span class="sxs-lookup"><span data-stu-id="c83f3-350">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="c83f3-351">Lecture de simulation de perception</span><span class="sxs-lookup"><span data-stu-id="c83f3-351">Perception Simulation Playback</span></span>

<span data-ttu-id="c83f3-352">**/API/Holographic/simulation/playback/file (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-352">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="c83f3-353">Supprimer un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-353">Delete a recording.</span></span>

<span data-ttu-id="c83f3-354">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-354">Parameters</span></span>
* <span data-ttu-id="c83f3-355">enregistrement : nom de l’enregistrement à supprimer.</span><span class="sxs-lookup"><span data-stu-id="c83f3-355">recording : Name of recording to delete.</span></span>

<span data-ttu-id="c83f3-356">**/API/Holographic/simulation/playback/file (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-356">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="c83f3-357">Télécharger un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-357">Upload a recording.</span></span>

<span data-ttu-id="c83f3-358">**/API/Holographic/simulation/playback/Files (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-358">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="c83f3-359">Récupération de tous les enregistrements.</span><span class="sxs-lookup"><span data-stu-id="c83f3-359">Get all recordings.</span></span>

<span data-ttu-id="c83f3-360">**/API/Holographic/simulation/playback/session (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-360">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="c83f3-361">Obtient l’état de lecture actuel d’un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-361">Get the current playback state of a recording.</span></span>

<span data-ttu-id="c83f3-362">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-362">Parameters</span></span>
* <span data-ttu-id="c83f3-363">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-363">recording : Name of recording.</span></span>

<span data-ttu-id="c83f3-364">**/API/Holographic/simulation/playback/session/file (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-364">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="c83f3-365">Décharger un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-365">Unload a recording.</span></span>

<span data-ttu-id="c83f3-366">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-366">Parameters</span></span>
* <span data-ttu-id="c83f3-367">enregistrement : nom de l’enregistrement à décharger.</span><span class="sxs-lookup"><span data-stu-id="c83f3-367">recording : Name of recording to unload.</span></span>

<span data-ttu-id="c83f3-368">**/API/Holographic/simulation/playback/session/file (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-368">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="c83f3-369">Charger un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-369">Load a recording.</span></span>

<span data-ttu-id="c83f3-370">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-370">Parameters</span></span>
* <span data-ttu-id="c83f3-371">enregistrement : nom de l’enregistrement à charger.</span><span class="sxs-lookup"><span data-stu-id="c83f3-371">recording : Name of recording to load.</span></span>

<span data-ttu-id="c83f3-372">**/API/Holographic/simulation/playback/session/Files (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-372">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="c83f3-373">Récupération de tous les enregistrements chargés.</span><span class="sxs-lookup"><span data-stu-id="c83f3-373">Get all loaded recordings.</span></span>

<span data-ttu-id="c83f3-374">**/API/Holographic/simulation/playback/session/pause (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-374">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="c83f3-375">Suspendre un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-375">Pause a recording.</span></span>

<span data-ttu-id="c83f3-376">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-376">Parameters</span></span>
* <span data-ttu-id="c83f3-377">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-377">recording : Name of recording.</span></span>

<span data-ttu-id="c83f3-378">**/API/Holographic/simulation/playback/session/Play (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-378">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="c83f3-379">Lire un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-379">Play a recording.</span></span>

<span data-ttu-id="c83f3-380">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-380">Parameters</span></span>
* <span data-ttu-id="c83f3-381">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-381">recording : Name of recording.</span></span>

<span data-ttu-id="c83f3-382">**/API/Holographic/simulation/playback/session/Stop (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-382">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="c83f3-383">Arrêter un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-383">Stop a recording.</span></span>

<span data-ttu-id="c83f3-384">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-384">Parameters</span></span>
* <span data-ttu-id="c83f3-385">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-385">recording : Name of recording.</span></span>

<span data-ttu-id="c83f3-386">**/API/Holographic/simulation/playback/session/types (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-386">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="c83f3-387">Obtenir les types de données dans un enregistrement chargé.</span><span class="sxs-lookup"><span data-stu-id="c83f3-387">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="c83f3-388">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-388">Parameters</span></span>
* <span data-ttu-id="c83f3-389">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-389">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="c83f3-390">Enregistrement de simulation de perception</span><span class="sxs-lookup"><span data-stu-id="c83f3-390">Perception Simulation Recording</span></span>

<span data-ttu-id="c83f3-391">**/API/Holographic/simulation/Recording/Start (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-391">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="c83f3-392">Démarrez un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-392">Start a recording.</span></span> <span data-ttu-id="c83f3-393">Un seul enregistrement peut être actif à la fois.</span><span class="sxs-lookup"><span data-stu-id="c83f3-393">Only a single recording can be active at once.</span></span> <span data-ttu-id="c83f3-394">Vous devez définir l’un des principaux, mains, spatialMapping ou environnement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-394">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="c83f3-395">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-395">Parameters</span></span>
* <span data-ttu-id="c83f3-396">Head : définissez sur 1 pour enregistrer les données de tête.</span><span class="sxs-lookup"><span data-stu-id="c83f3-396">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="c83f3-397">mains : définissez sur 1 pour enregistrer les données de la main.</span><span class="sxs-lookup"><span data-stu-id="c83f3-397">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="c83f3-398">spatialMapping : affectez la valeur 1 pour enregistrer le mappage spatial.</span><span class="sxs-lookup"><span data-stu-id="c83f3-398">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="c83f3-399">environnement : définissez sur 1 pour enregistrer les données d’environnement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-399">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="c83f3-400">nom : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-400">name : Name of the recording.</span></span>
* <span data-ttu-id="c83f3-401">singleSpatialMappingFrame : affectez la valeur 1 pour enregistrer uniquement un seul frame de mappage spatial.</span><span class="sxs-lookup"><span data-stu-id="c83f3-401">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="c83f3-402">**/API/Holographic/simulation/Recording/Status (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-402">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="c83f3-403">Obtient l’état de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c83f3-403">Get recording state.</span></span>

<span data-ttu-id="c83f3-404">**/API/Holographic/simulation/Recording/Stop (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-404">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="c83f3-405">Arrêter l’enregistrement en cours.</span><span class="sxs-lookup"><span data-stu-id="c83f3-405">Stop the current recording.</span></span> <span data-ttu-id="c83f3-406">L’enregistrement est retourné sous la forme d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="c83f3-406">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="c83f3-407">Données de performances</span><span class="sxs-lookup"><span data-stu-id="c83f3-407">Performance data</span></span>

<span data-ttu-id="c83f3-408">**/API/ResourceManager/Processes (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-408">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="c83f3-409">Retourne la liste des processus en cours d’exécution avec les détails</span><span class="sxs-lookup"><span data-stu-id="c83f3-409">Returns the list of running processes with details</span></span>

<span data-ttu-id="c83f3-410">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="c83f3-410">Return data</span></span>
* <span data-ttu-id="c83f3-411">JSON avec liste de processus et détails pour chaque processus</span><span class="sxs-lookup"><span data-stu-id="c83f3-411">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="c83f3-412">**/API/ResourceManager/systemperf (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-412">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="c83f3-413">Retourne les statistiques de performances système (lecture/écriture d’e/s, statistiques de mémoire, etc.).</span><span class="sxs-lookup"><span data-stu-id="c83f3-413">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="c83f3-414">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="c83f3-414">Return data</span></span>
* <span data-ttu-id="c83f3-415">JSON avec informations système : processeur, GPU, mémoire, réseau, e/s</span><span class="sxs-lookup"><span data-stu-id="c83f3-415">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="c83f3-416">Power</span><span class="sxs-lookup"><span data-stu-id="c83f3-416">Power</span></span>

<span data-ttu-id="c83f3-417">**/API/Power/Battery (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-417">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="c83f3-418">Obtient l’état actuel de la batterie</span><span class="sxs-lookup"><span data-stu-id="c83f3-418">Gets the current battery state</span></span>

<span data-ttu-id="c83f3-419">**/API/Power/State (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-419">**/api/power/state (GET)**</span></span>

<span data-ttu-id="c83f3-420">Vérifie si le système est dans un état de faible consommation d’énergie.</span><span class="sxs-lookup"><span data-stu-id="c83f3-420">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="c83f3-421">Contrôle à distance</span><span class="sxs-lookup"><span data-stu-id="c83f3-421">Remote Control</span></span>

<span data-ttu-id="c83f3-422">**/API/Control/Restart (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-422">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="c83f3-423">Redémarre l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="c83f3-423">Restarts the target device</span></span>

<span data-ttu-id="c83f3-424">**/API/Control/Shutdown (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-424">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="c83f3-425">Arrête l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="c83f3-425">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="c83f3-426">Gestionnaire des tâches</span><span class="sxs-lookup"><span data-stu-id="c83f3-426">Task Manager</span></span>

<span data-ttu-id="c83f3-427">**/API/taskmanager/App (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-427">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="c83f3-428">Arrête une application moderne</span><span class="sxs-lookup"><span data-stu-id="c83f3-428">Stops a modern app</span></span>

<span data-ttu-id="c83f3-429">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-429">Parameters</span></span>
* <span data-ttu-id="c83f3-430">Package : nom complet du package d’application, hex64 encodé</span><span class="sxs-lookup"><span data-stu-id="c83f3-430">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="c83f3-431">forceStop : force l’arrêt de tous les processus (= oui)</span><span class="sxs-lookup"><span data-stu-id="c83f3-431">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="c83f3-432">**/API/taskmanager/App (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-432">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="c83f3-433">Démarre une application moderne</span><span class="sxs-lookup"><span data-stu-id="c83f3-433">Starts a modern app</span></span>

<span data-ttu-id="c83f3-434">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-434">Parameters</span></span>
* <span data-ttu-id="c83f3-435">AppID : PRAID de l’application à démarrer, hex64 encodé</span><span class="sxs-lookup"><span data-stu-id="c83f3-435">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="c83f3-436">Package : nom complet du package d’application, hex64 encodé</span><span class="sxs-lookup"><span data-stu-id="c83f3-436">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="c83f3-437">Gestion WiFi</span><span class="sxs-lookup"><span data-stu-id="c83f3-437">WiFi Management</span></span>

<span data-ttu-id="c83f3-438">**/API/WiFi/interfaces (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-438">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="c83f3-439">Énumère les interfaces de réseau sans fil</span><span class="sxs-lookup"><span data-stu-id="c83f3-439">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="c83f3-440">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="c83f3-440">Return data</span></span>
* <span data-ttu-id="c83f3-441">Liste des interfaces sans fil avec des détails (GUID, description, etc.)</span><span class="sxs-lookup"><span data-stu-id="c83f3-441">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="c83f3-442">**/API/WiFi/Network (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-442">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="c83f3-443">Supprime un profil associé à un réseau sur une interface spécifiée</span><span class="sxs-lookup"><span data-stu-id="c83f3-443">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="c83f3-444">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-444">Parameters</span></span>
* <span data-ttu-id="c83f3-445">Interface : GUID de l’interface réseau</span><span class="sxs-lookup"><span data-stu-id="c83f3-445">interface : network interface guid</span></span>
* <span data-ttu-id="c83f3-446">Profil : nom du profil</span><span class="sxs-lookup"><span data-stu-id="c83f3-446">profile : profile name</span></span>

<span data-ttu-id="c83f3-447">**/API/WiFi/Networks (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-447">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="c83f3-448">Énumère les réseaux sans fil sur l’interface réseau spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c83f3-448">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="c83f3-449">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-449">Parameters</span></span>
* <span data-ttu-id="c83f3-450">Interface : GUID de l’interface réseau</span><span class="sxs-lookup"><span data-stu-id="c83f3-450">interface : network interface guid</span></span>

<span data-ttu-id="c83f3-451">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="c83f3-451">Return data</span></span>
* <span data-ttu-id="c83f3-452">Liste des réseaux sans fil détectés sur l’interface réseau avec les détails</span><span class="sxs-lookup"><span data-stu-id="c83f3-452">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="c83f3-453">**/API/WiFi/Network (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-453">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="c83f3-454">Se connecte ou se déconnecte à un réseau sur l’interface spécifiée</span><span class="sxs-lookup"><span data-stu-id="c83f3-454">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="c83f3-455">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-455">Parameters</span></span>
* <span data-ttu-id="c83f3-456">Interface : GUID de l’interface réseau</span><span class="sxs-lookup"><span data-stu-id="c83f3-456">interface : network interface guid</span></span>
* <span data-ttu-id="c83f3-457">SSID : SSID, hex64 encodé, pour se connecter à</span><span class="sxs-lookup"><span data-stu-id="c83f3-457">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="c83f3-458">opération : se connecter ou se déconnecter</span><span class="sxs-lookup"><span data-stu-id="c83f3-458">op : connect or disconnect</span></span>
* <span data-ttu-id="c83f3-459">CreateProfile : oui ou non</span><span class="sxs-lookup"><span data-stu-id="c83f3-459">createprofile : yes or no</span></span>
* <span data-ttu-id="c83f3-460">clé : clé partagée, encodée en hex64</span><span class="sxs-lookup"><span data-stu-id="c83f3-460">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="c83f3-461">Enregistreur de performances Windows</span><span class="sxs-lookup"><span data-stu-id="c83f3-461">Windows Performance Recorder</span></span>

<span data-ttu-id="c83f3-462">**/API/WPR/customtrace (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-462">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="c83f3-463">Charge un profil WPR et démarre le suivi à l’aide du profil chargé.</span><span class="sxs-lookup"><span data-stu-id="c83f3-463">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="c83f3-464">Payload</span><span class="sxs-lookup"><span data-stu-id="c83f3-464">Payload</span></span>
* <span data-ttu-id="c83f3-465">corps http en plusieurs parties, conforme</span><span class="sxs-lookup"><span data-stu-id="c83f3-465">multi-part conforming http body</span></span>

<span data-ttu-id="c83f3-466">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="c83f3-466">Return data</span></span>
* <span data-ttu-id="c83f3-467">Retourne l’état de la session WPR.</span><span class="sxs-lookup"><span data-stu-id="c83f3-467">Returns the WPR session status.</span></span>

<span data-ttu-id="c83f3-468">**/API/WPR/Status (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-468">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="c83f3-469">Récupère l’état de la session WPR</span><span class="sxs-lookup"><span data-stu-id="c83f3-469">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="c83f3-470">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="c83f3-470">Return data</span></span>
* <span data-ttu-id="c83f3-471">État de session WPR.</span><span class="sxs-lookup"><span data-stu-id="c83f3-471">WPR session status.</span></span>

<span data-ttu-id="c83f3-472">**/API/WPR/trace (récupération)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-472">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="c83f3-473">Arrête une session de suivi WPR (performance)</span><span class="sxs-lookup"><span data-stu-id="c83f3-473">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="c83f3-474">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="c83f3-474">Return data</span></span>
* <span data-ttu-id="c83f3-475">Retourne le fichier ETL de trace</span><span class="sxs-lookup"><span data-stu-id="c83f3-475">Returns the trace ETL file</span></span>

<span data-ttu-id="c83f3-476">**/API/WPR/trace (publication)**</span><span class="sxs-lookup"><span data-stu-id="c83f3-476">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="c83f3-477">Démarre une session de suivi WPR (performance)</span><span class="sxs-lookup"><span data-stu-id="c83f3-477">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="c83f3-478">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c83f3-478">Parameters</span></span>
* <span data-ttu-id="c83f3-479">Profil : nom du profil.</span><span class="sxs-lookup"><span data-stu-id="c83f3-479">profile : Profile name.</span></span> <span data-ttu-id="c83f3-480">Les profils disponibles sont stockés dans perfprofiles/profiles.jssur</span><span class="sxs-lookup"><span data-stu-id="c83f3-480">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="c83f3-481">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="c83f3-481">Return data</span></span>
* <span data-ttu-id="c83f3-482">Dans Démarrer, retourne l’état de la session WPR.</span><span class="sxs-lookup"><span data-stu-id="c83f3-482">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="c83f3-483">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c83f3-483">See also</span></span>
* [<span data-ttu-id="c83f3-484">Utilisation du portail d’appareil Windows</span><span class="sxs-lookup"><span data-stu-id="c83f3-484">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="c83f3-485">Informations de référence sur l’API principale du portail des appareils (UWP)</span><span class="sxs-lookup"><span data-stu-id="c83f3-485">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
