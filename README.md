# temp
A = imread('image.png');[L,N] = superpixels(A,500);[row, col, layer] = size(A);figureBW = boundarymask(L);imshow(imoverlay(A,BW,'cyan'),'InitialMagnification',67);outputImage = zeros(size(A),'like',A);idx = label2idx(L);numRows = size(A,1);numCols = size(A,2);superpixel = {};im = im2single(A);for labelVal = 1:N    redIdx = idx{labelVal};    greenIdx = idx{labelVal}+numRows*numCols;    blueIdx = idx{labelVal}+2*numRows*numCols;        outputImage(redIdx) = mean(A(redIdx));      outputImage(greenIdx) = mean(A(greenIdx));      outputImage(blueIdx) = mean(A(blueIdx));             superpixel{labelVal}(:,1) = fix((redIdx-1)/numRows)+1;     superpixel{labelVal}(:,2) = rem(redIdx-1,numRows)+1;     superpixel{labelVal}(:,3) = im(redIdx);     superpixel{labelVal}(:,4) = im(redIdx);     superpixel{labelVal}(:,5) = im(redIdx); end    figure imshow(outputImage,'InitialMagnification',67)
