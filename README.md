# Scripss_FF_V
/**
 * PROJECT: HK MASTER V14 - M1014 EDITION
 * OPTIMIZED FOR: iPhone 15 Pro Max
 */

async function onResponse(request, response) {
    let body = response.body;

    // --- FILTRO DE SEGURIDAD ---
    if (url.includes("geotrust") || url.includes("report")) return response;

    // --- PODER INYECTOR M1014 (-500) ---
    if (url.includes("com.dts.freefire") || url.includes("weapon")) {
        try {
            // HITBOX GIGANTE (Koder te permite editar este valor rápido)
            body = body.replace(/"HeadRadius":\s*[\d.]+/g, '"HeadRadius": 125.0');
            
            // CONCENTRACIÓN LÁSER (M1014 Sin Dispersión)
            body = body.replace(/"max_spread":\s*[\d.]+/g, '"max_spread": 0.0');
            body = body.replace(/"shot_spread":\s*[\d.]+/g, '"shot_spread": 0.0');
            
            // DAÑO CRÍTICO MAX (-500)
            body = body.replace(/"damage_multiplier":\s*[\d.]+/g, '"damage_multiplier": 99.0');
            body = body.replace(/"headshot_mult":\s*[\d.]+/g, '"headshot_mult": 45.0');
            
            // BALAS MÁGICAS ACTIVAS
            body = body.replace(/"magic_bullet":\s*\w+/g, '"magic_bullet": true');

            response.body = body;
            console.log("💎 KODER INJECTOR V14: M1014 CARGADA");
        } catch (e) {
            console.log("Error en inyección: " + e);
        }
    }
    return response;
}
