# Filtering-cases-and-subgroups-in-r-programming
# Filtering cases and subgroup data in R  
### make sure to install all the packages below. 
install.packages("tidyverse")
pacman::p_load(pacman, tidyverse, rio)

data <- import("stateData.xlsx") %>% as_tibble()%>%
  select(state_code, region, psychRegions, instagram:modernDance) %>%
  print()

view(data)  

attach(data)
### histogram for entrepreneur
qplot(entrepreneur, geom = "histogram", data = data)

###  filtering entrepreneur from above 1
data1 <- data %>% filter(entrepreneur > 1) %>% print()
view(data1)

### Region is  character variable 
qplot(region, data  = data)

#### looking for th states in the south 
data %>% filter(region == "South")

### looking for all the states whose psyvhregion is Relaxed and creative 
qplot(psychRegions, data = data)
data %>% filter(psychRegions == "Relaxed and Creative") %>% print()


### filtering by and or and not 
data %>% filter(region == "North" | psychRegions == "Friendly and Conventional")
data %>% filter(region == "South" & psychRegions == "Relaxed and Creative")
data %>% filter(!region == "South" & psychRegions == "Relaxed and Creative")
