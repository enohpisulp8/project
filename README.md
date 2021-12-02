#include <stdio.h>

int main() {
    char traits[4][8][15] = {
        {"passive", "careful", "thoughtful", "peaceful", "controlled", "reliable", "even-tempered", "calm"},
        {"leadership", "carefree", "lively", "easygoing", "responsive", "talkative", "outgoing", "sociable"},
        {"active", "optimistic", "impulsive", "changeable", "excitable", "aggressive", "restless", "touchy"},
        {"moody", "anxious", "rigid", "sober", "pessimistic", "reserved", "unsociable", "quiet"}
    };
    char temperaments[4][15] = {"Phlegmatic", "Sanguine", "Choleric", "Melancholic"};
    
    printf("Welcome to 4 temperaments test.\nAnswer based on you when you are normally being yourself, Put 1 for yes. Put 0 for no.\n\n");
    
    while (1) {
        int pscm[4] = {0, 0, 0, 0};
        for (int i = 0; i < 4; i++) {
            for (int j = 0; j < 8; j++) {
                int v;
                do {
                    printf("%s: ", traits[i][j]);
                    scanf("%d", &v);
                } while (v != 1 && v != 0);
                if (v) pscm[i]++;
            }
        }
        
        int max1 = 0, max2 = 0, mi1 = 0, mi2 = 0;
        
        for(int i = 0; i < 4; i++) {
            if (pscm[i] >= max1) {
                mi2 = mi1;
                max2 = max1;
                mi1 = i;
                max1 = pscm[i];
            }
            else if (pscm[i] >= max2 && pscm[i] <= max1) {
                mi2 = i;
                max2 = pscm[i];
            }
        }
        
        printf("----------------------------------------------------------------\nYour temperaments are: %s-%s\n\n", temperaments[mi1], temperaments[mi2]);
        
        int more = 0; 
        printf("Do you want to do the test again?(1 for yes): ");
        scanf("%d", &more);
        if (more != 1) return 0;
    }
}
