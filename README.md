
# 无人机

标签（空格分隔）： 无人机

---

```
#include<stdio.h>
#include<stdlib.h>

#define MAX_INPUT_SIZE 10000

int GennerateMap(int height, int width, char map[], char output[]){
    int count = 0;
    int count1 = 0;
    int flag = 0;
    if(width>100||width<0||height>100||height<0){
        return -1;
    }
    while(map[count] != '\0' && map[count] != '\002'){
        if(map[count] != 'G' && map[count] != 'F' && map[count] != 'R'){
            return -2;
        }
        if(flag ==1){
            output[count1] = '\n';
            count1++;
            flag = 0;
        } else {
            output[count1] = map[count];                        
            count1++;
            count++;
            if(count % width == 0){
                flag = 1;
            }
        }
    }
    if(count != (width*height)){
        return -3;
    }
    output[count1] = '\0';
    return 0; 
}
int main(){
    int a, b, i, ch;
    char map[MAX_INPUT_SIZE];
    char output[MAX_INPUT_SIZE];
    int result = 0;
    scanf("%d %d \n", &a, &b);
    for (i = 0; i < sizeof(map) - 1 && (ch = getchar()) != EOF && ch != '\n'; i++){
        map[i] = ch;
    }
    result = GennerateMap(a, b, map, output);

    if (result == -1)
    {
        printf("Incorrect mesh size! \n");
    }

    if(result == -2){
        printf("Invalid cell type! \n");
    }

    if(result == -3){
        printf("Data mismatch \n");
    }

    if(result == 0 && output != NULL)
    {
        printf("%s\n", output);
    }
    system("pause");
    return 0;
}

 - 列表项

```




