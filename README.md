import cv2
import numpy

cam = cv2.VideoCapture(0)

while True:
    ret, frame = cam.read()
    width = int(cam.get(3))
    height = int(cam.get(4))
    small_cam = cv2.resize(frame,(0,0),fx=0.5,fy=0.5)
    image = numpy.zeros(frame.shape, numpy.uint8)
    image[None:height//2, None:width//2] = small_cam
    image[height//2:None, width//2:None] = small_cam
    image[height//2:None, None:width//2] = small_cam
    image[None:height//2, width//2:None] = small_cam


    cv2.imshow("Test_1",image)
    if cv2.waitKey(1) == ord('q'):
        break

cam.release()
cv2.destroyAllWindows()
